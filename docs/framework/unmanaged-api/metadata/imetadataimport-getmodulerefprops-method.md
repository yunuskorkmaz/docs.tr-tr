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
ms.openlocfilehash: 606a3f2cfba05b014960842c5db77149f449193d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733133"
---
# <a name="imetadataimportgetmodulerefprops-method"></a>IMetaDataImport::GetModuleRefProps Yöntemi

Belirtilen meta veri belirtecinin başvurduğu modülün adını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Meta veri bilgilerini almak için modüle başvuruda bulunan ModuleRef meta veri belirteci.  
  
 `szName`  
 dışı Modül adını tutan bir arabellek.  
  
 `cchName`  
 'ndaki `szName` Geniş karakter olarak istenen boyutu.  
  
 `pchName`  
 dışı `szName` Geniş karakter olarak döndürülen boyutu.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
