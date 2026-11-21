# E-Commerce Platform with Odoo ERP/CRM Integration

Academic project developed for the **Organizational and Management Systems 1** course at the Universidad de San Carlos de Guatemala (Second Semester 2026).

This repository implements a full e-commerce platform integrated in real time with an Odoo 14 ERP/CRM instance hosted on Microsoft Azure. The project was developed collaboratively as a group assignment.

---

## Overview

The system consists of a React + TypeScript storefront connected through a FastAPI middleware layer to Odoo via XML-RPC. Every purchase triggers automated workflows across CRM leads, sales orders, inventory dispatching, and electronic invoicing — all without manual intervention.

---

## Key Features

- Product catalog with search, filters, and persistent cart
- Customer registration and quotation management
- Simulated payment processing with tokenized cards
- Bidirectional real-time synchronization with Odoo:
  - CRM (`crm.lead`): records each purchase attempt as a won opportunity
  - ERP Sales (`sale.order`): confirms the sales order automatically
  - Inventory (`stock.picking`): decrements stock and generates dispatch orders
  - Accounting (`account.move`): publishes the customer invoice on purchase
- Customer portal for reviewing orders, quotes, invoices, and payments
- Automated test suite covering API contracts and end-to-end flow

---

## Architecture

```
[ Web Storefront (React + TypeScript) ]
            |  REST / JSON
            v
   [ FastAPI Middleware (port 8000) ]
            |  XML-RPC
            v
   [ Odoo 14 + PostgreSQL 13 on Azure (port 8069) ]
      ├── res.partner      (Customers)
      ├── crm.lead         (CRM Opportunities)
      ├── sale.order       (Sales Orders)
      ├── stock.picking    (Inventory Dispatch)
      └── account.move     (Electronic Invoices)
```

---

## Technologies

- **Frontend:** TypeScript, React, Vite, Zustand
- **Backend:** Python, FastAPI, XML-RPC
- **ERP/CRM:** Odoo 14
- **Database:** PostgreSQL 13
- **Cloud:** Microsoft Azure
- **Testing:** Python unittest

---

## Repository Structure

```
ecommerce-erp-odoo-integration/
├── backend/
│   ├── config.py          # Odoo connection settings
│   ├── odoo_client.py     # XML-RPC client for ERP/CRM/Stock/Invoicing
│   ├── main.py            # FastAPI server with REST endpoints
│   └── requirements.txt
├── frontend/
│   └── src/
│       ├── components/    # Navigation, products, forms, cart
│       ├── pages/         # Catalog, account, quotation, portal
│       ├── lib/api.ts     # Typed API client
│       └── store/         # Persistent state (Zustand)
├── tests/
│   ├── test_api.py        # Isolated API contract tests
│   └── test_flow.py       # End-to-end integration test
└── docs/
    ├── manual_tecnico_integracion.md
    └── manual_usuario_ecommerce.md
```

---

## Academic Context

| Field       | Detail                                              |
|-------------|-----------------------------------------------------|
| Course      | Organizational and Management Systems 1 (GEREN1)   |
| Institution | Universidad de San Carlos de Guatemala              |
| Semester    | Second Semester 2026                                |
| Type        | Group project                                       |
