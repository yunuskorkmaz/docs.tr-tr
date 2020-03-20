---
title: IMetaDataEmit::DefinePermissionSet Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: a0fd3fdb6dde9fd6b88ea6c64ed907c8a3e9e46d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175804"
---
# <a name="imetadataemitdefinepermissionset-method"></a>IMetaDataEmit::DefinePermissionSet Yöntemi
Belirtilen meta veri imzasıyla bir izin kümesi için tanım oluşturur ve bu izin kümesi tanımına bir belirteç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 [içinde] Dekore edilecek nesne.  
  
 `dwAction`  
 [içinde] Kullanılacak bildirimsel güvenlik türünü belirten bir [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) değeri.  
  
 `pvPermission`  
 [içinde] İzin BLOB.  
  
 `cbPermission`  
 [içinde] Boyutu, bayt, ve. `pvPermission`  
  
 `ppm`  
 [çıkış] İade edilen izin jetonu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
