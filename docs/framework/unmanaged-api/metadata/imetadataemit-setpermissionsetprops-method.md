---
description: ': Imetadatayayma:: SetPermissionSetProps Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1e2786a21a1024f32328e36878a1a2427af54f51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771892"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a>IMetaDataEmit::SetPermissionSetProps Yöntemi

[Imetadatayayma::D efinePermissionSet](imetadataemit-definepermissionset-method.md)için önceki bir çağrı tarafından tanımlanan izin kümesinin meta veri imzasının özelliklerini ayarlar veya güncelleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
