# Naming Conventions
Naming conventions used.

**DDIC Artifacts**

| DDIC Artifacts                            | Naming Convention | Length      |
| :---------------------------------------- | :---------------- | ----------: |
| Namespace                                 | ZVKS              |             |
| Domain                                    | ZVKS_DO_*         |             |
| Data Element                              | ZVKS_DE_*         |             |
| Persistent Database Table (Active)        | ZVKS_A_*          |             |
| Draft Database Table                      | ZVKS_D_*          |             |

**Interface View**
 
| View Type                                 | Naming Convention | Length      |
| :---------------------------------------- | :---------------- | ----------: |
| Basic View (Restrictive)                  | ZVKS_R_*          |             |
| Composite View (Value Help)               | ZVKS_I_*_VH       |             |
| Composite View (Trxn processing)          | ZVKS_I_*_TP       |             |

**Consumption View**

| View Type                                 | Naming Convention | Length      |
| :---------------------------------------- | :---------------- | ----------: |
| Consumption View (Read Only)              | ZVKS_C_*_R        |             |
| Projection View (TP Managed - Default)    | ZVKS_C_*_M        |             |
| Projection View (TP Managed - Manager)    | ZVKS_C_*_M_MNG    |             |
| Projection View (TP Managed - Approver)   | ZVKS_C_*_M_APR    |             |
| Projection View (TP Managed - Analyst)    | ZVKS_C_*_M_ANA    |             |
| Projection View (TP Unmanaged - Default)  | ZVKS_C_*_U        |             |
| Projection View (TP Unmanaged - Manager)  | ZVKS_C_*_U_MNG    |             |
| Projection View (TP Unmanaged - Approver) | ZVKS_C_*_U_APR    |             |
| Projection View (TP Unmanaged - Analyst)  | ZVKS_C_*_U_ANA    |             |

**Business Services**

| Business Service Name                     | Naming Convention | Length      |
| :---------------------------------------- | :---------------- | ----------: |
| Service Definition                        | ZVKS_SD_*_V(N)    |             |
| Service Binding (OData V2)                | ZVKS_UI_*_O2      |             |
| Service Binding (OData V4)                | ZVKS_UI_*_O4      |             |
| Service Binding (Web API)                 | ZVKS_API_*_R(N)   |             |
| Behaviour Definition                      | ZVKS_SD_*_R        |             |
| Behaviour Implementation                  | ZVKS_SD_*_R        |             |

| Development Objects                | Naming Convention | Length      |
| :--------------------------------- | :---------------- | ----------: |
| Global Class                       | ZVKS_CL_*         |             |
| Structure Type                     | GTY/LTY_ST_*      |             |
| Table Type                         | GTY/LTY_TT_*      |             |
