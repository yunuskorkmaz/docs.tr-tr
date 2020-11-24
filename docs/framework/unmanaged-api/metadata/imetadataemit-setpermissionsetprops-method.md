---
title: IMetaDataEmit::SetPermissionSetProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: 4c3e0953d71020ba62ee4ab68aa9e21ea3f0f521
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675041"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a>IMetaDataEmit::SetPermissionSetProps Yöntemi

[Imetadatayayma::D efinePermissionSet](imetadataemit-definepermissionset-method.md)için önceki bir çağrı tarafından tanımlanan izin kümesinin meta veri imzasının özelliklerini ayarlar veya güncelleştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `tk`  
 'ndaki Tasarlankullanılacak nesneyi temsil eden bir meta veri belirteci.  
  
 `dwAction`  
 'ndaki Kullanılacak bildirime dayalı güvenlik türünü belirten bir [CorDeclSecurity](cordeclsecurity-enumeration.md) değeri.  
  
 `pvPermission`  
 'ndaki İzin blobu.  
  
 `cbPermission`  
 'ndaki Bayt cinsinden boyutu `pvPermission` .  
  
 `ppm`  
 dışı `mdPermission` Güncelleştirilmiş izinleri temsil eden bir meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
