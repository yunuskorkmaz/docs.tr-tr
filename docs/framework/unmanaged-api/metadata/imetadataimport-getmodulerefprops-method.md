---
title: IMetaDataImport::GetModuleRefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: f46033b9e643ef6b4a0063c4995b8c024b8c1f7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175362"
---
# <a name="imetadataimportgetmodulerefprops-method"></a>IMetaDataImport::GetModuleRefProps Yöntemi
Belirtilen meta veri belirteci tarafından başvurulan modülün adını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `mur`  
 [içinde] Modüliçin meta veri bilgisi almak için modüle başvuran ModuleRef meta veri belirteci.  
  
 `szName`  
 [çıkış] Modül adını tutmak için bir arabellek.  
  
 `cchName`  
 [içinde] Geniş karakterlerde `szName` istenen boyutu.  
  
 `pchName`  
 [çıkış] Geniş karakterlerde `szName` döndürülen boyutu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
