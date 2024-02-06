# Naming Conventions

https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/ee6ff9b281d8448f96b4fe6c89f2bdc8/8a8cee943ef944fe8936f4cc60ba9bc1.html

**DDIC Artifacts**

| DDIC Artifacts                            | Naming Convention         | Length      |
| :---------------------------------------- | :----------------------   | ----------: |
| Namespace                                 | ZVKS                      |             |
| Domain                                    | ZVKS_DO_DOMAIN_NAME       |             |
| Data Element                              | ZVKS_DE_DATA_ELEMENT_NAME |             |
| Persistent Database Table (Active)        | ZVKS_A_TABLE_NAME         |             |
| Draft Database Table                      | ZVKS_D_TABLE_NAME         |             |

**Interface View**
 
| View Type                                 | Naming Convention  | Length      |
| :---------------------------------------- | :----------------- | ----------: |
| Namespace                                 | ZVKS               |             |
| Basic View (Restrictive)                  | ZVKS_R_ViewName    |             |
| Composite View (Addional Logic)           | ZVKS_I_ViewName    |             |
| Composite View (Value Help)               | ZVKS_I_ViewName_VH |             |
| Composite View (Text)                     | ZVKS_I_ViewName_T  |             |
| Composite View (Trxn processing)          | ZVKS_I_ViewName_TP |             |

**Consumption View**

| View Type                                 | Naming Convention     | Length      |
| :---------------------------------------- | :-------------------- | ----------: |
| Namespace                                 | ZVKS                  |             |
| Consumption View (Read Only)              | ZVKS_C_ViewName_R     |             |
| Projection View (TP Managed - Default)    | ZVKS_C_ViewName_M     |             |
| Projection View (TP Managed - Manager)    | ZVKS_C_ViewName_M_MNG |             |
| Projection View (TP Managed - Approver)   | ZVKS_C_ViewName_M_APR |             |
| Projection View (TP Managed - Analyst)    | ZVKS_C_ViewName_M_ANA |             |
| Projection View (TP Unmanaged - Default)  | ZVKS_C_ViewName_U     |             |
| Projection View (TP Unmanaged - Manager)  | ZVKS_C_ViewName_U_MNG |             |
| Projection View (TP Unmanaged - Approver) | ZVKS_C_ViewName_U_APR |             |
| Projection View (TP Unmanaged - Analyst)  | ZVKS_C_ViewName_U_ANA |             |

**Auxiliary View**

| View Type                                 | Naming Convention              | Length      |
| :---------------------------------------- | :------------------------------| ----------: |
| Namespace                                 | ZVKS                           |             |
| Extension View                            | ZVKS_X_ReferenceViewName       |             |
| Metadata Extension View (MDE)             | ZVKS_E_ReferenceViewName       |             |

**Other Objects**

| Object                                 | Naming Convention              | Length      |
| :---------------------------------------- | :-------------------------- | ----------: |
| Namespace                                 | ZVKS                        |             |
| Knowledge Transfer Object (KTD)           | ZVKS_K_ReferenceObjectName  |             |

**Annotations**

| View Type                                 | Naming Convention     | Length      |
| :---------------------------------------- | :-------------------- | ----------: |
| Facet - id                                | idIdentifier          |             |
| Face - targetQualifier                    | tqIdentifier          |             |

**Business Services**

| Business Service Name                     | Naming Convention           | Length      |
| :---------------------------------------- | :-------------------------- | ----------: |
| Behaviour Definition                      | -                           |             |
| Behaviour Implementation Class            | ZVKS_BP_ViewName            |             |
| Service Definition                        | ZVKS_SD_ServiceName_(N)     |             |
| Service Binding (OData V2)                | ZVKS_UI_ServiceName_O2_(N)  |             |
| Service Binding (OData V4)                | ZVKS_UI_ServiceName_O4_(N)  |             |
| Service Binding (Web API)                 | ZVKS_API_ServiceName_V(N)   |             |

| Development Objects                | Naming Convention | Length      |
| :--------------------------------- | :---------------- | ----------: |
| Global Class                       | ZVKS_CL_*         |             |
| Structure Type                     | GTY/LTY_ST_*      |             |
| Table Type                         | GTY/LTY_TT_*      |             |
