---
title: IMetaDataImport::GetPermissionSetProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
ms.openlocfilehash: 54c75156c32e5b40aa933ef6530b2cc33edf7de4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490997"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a>IMetaDataImport::GetPermissionSetProps Yöntemi
<xref:System.Security.PermissionSet?displayProperty=nameWithType>Belirtilen izin belirteciyle temsil edilen ile ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pm`  
 'ndaki Meta veri özelliklerini almak için ayarlanan izni temsil eden Izin meta veri belirteci.  
  
 `pdwAction`  
 dışı İzin kümesine yönelik bir işaretçi.  
  
 `ppvPermission`  
 dışı İzin kümesinin ikili meta veri imzasına yönelik bir işaretçi.  
  
 `pcbPermission`  
 dışı Bayt cinsinden boyut `ppvPermission` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.PermissionSet>
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
