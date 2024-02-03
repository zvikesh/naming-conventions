# Naming Conventions

https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/ee6ff9b281d8448f96b4fe6c89f2bdc8/8a8cee943ef944fe8936f4cc60ba9bc1.html

**DDIC Artifacts**

| DDIC Artifacts                            | Naming Convention       | Length      |
| :---------------------------------------- | :---------------------- | ----------: |
| Namespace                                 | ZVKS                    |             |
| Domain                                    | ZVKS_DO_DomainName      |             |
| Data Element                              | ZVKS_DE_DataElementName |             |
| Persistent Database Table (Active)        | ZVKS_A_TableName        |             |
| Draft Database Table                      | ZVKS_D_TableName        |             |

**Interface View**
 
| View Type                                 | Naming Convention  | Length      |
| :---------------------------------------- | :----------------- | ----------: |
| Basic View (Restrictive)                  | ZVKS_R_ViewName    |             |
| Composite View (Value Help)               | ZVKS_I_ViewName_VH |             |
| Composite View (Trxn processing)          | ZVKS_I_ViewName_TP |             |

**Consumption View**

| View Type                                 | Naming Convention     | Length      |
| :---------------------------------------- | :-------------------- | ----------: |
| Consumption View (Read Only)              | ZVKS_C_ViewName_R     |             |
| Projection View (TP Managed - Default)    | ZVKS_C_ViewName_M     |             |
| Projection View (TP Managed - Manager)    | ZVKS_C_ViewName_M_MNG |             |
| Projection View (TP Managed - Approver)   | ZVKS_C_ViewName_M_APR |             |
| Projection View (TP Managed - Analyst)    | ZVKS_C_ViewName_M_ANA |             |
| Projection View (TP Unmanaged - Default)  | ZVKS_C_ViewName_U     |             |
| Projection View (TP Unmanaged - Manager)  | ZVKS_C_ViewName_U_MNG |             |
| Projection View (TP Unmanaged - Approver) | ZVKS_C_ViewName_U_APR |             |
| Projection View (TP Unmanaged - Analyst)  | ZVKS_C_ViewName_U_ANA |             |

**Annotation**
| View Type                                 | Naming Convention     | Length      |
| :---------------------------------------- | :-------------------- | ----------: |
| Facet - id                                | idIdentifier          |             |
| Face - targetQualifier                    | tqIdentifier          |             |

**Business Services**

| Business Service Name                     | Naming Convention                  | Length      |
| :---------------------------------------- | :--------------------------------- | ----------: |
| Service Definition                        | ZVKS_SD_ViewName_ViewSuffix_(N)    |             |
| Service Binding (OData V2)                | ZVKS_UI_ViewName_ViewSuffix_O2_(N) |             |
| Service Binding (OData V4)                | ZVKS_UI_ViewName_ViewSuffix_O4_(N) |             |
| Service Binding (Web API)                 | ZVKS_API_*_V(N)              |             |
| Behaviour Definition                      | ZVKS_SD_*_R        |             |
| Behaviour Implementation                  | ZVKS_SD_*_R        |             |

| Development Objects                | Naming Convention | Length      |
| :--------------------------------- | :---------------- | ----------: |
| Global Class                       | ZVKS_CL_*         |             |
| Structure Type                     | GTY/LTY_ST_*      |             |
| Table Type                         | GTY/LTY_TT_*      |             |
