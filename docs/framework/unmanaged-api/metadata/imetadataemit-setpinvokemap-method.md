---
title: IMetaDataEmit::SetPinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 4c68754bc44fe035fd8e7143c52895928beae395
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175596"
---
# <a name="imetadataemitsetpinvokemap-method"></a>IMetaDataEmit::SetPinvokeMap Yöntemi
Bir yöntemin PInvoke imzasının özelliklerini ayarlar veya değiştirir, [iMetaDataEmit::DefinePinvokeMap.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 [içinde] Haritalama bilgilerinin `mdToken` uygulandığı yer.  
  
 `dwMappingFlags`  
 [içinde] Eşleme yapmak için PInvoke tarafından kullanılan bayraklar. Bu `CorPinvokeMap` değerlerin bir bitmask olduğunu.  
  
 `szImportName`  
 [içinde] Yerel DLL'deki hedef dışa aktarmanın adı.  
  
 `mrImportDLL`  
 [içinde] Hedef `mdModuleRef` in belirteç leri yönetilmemiş DLL.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
