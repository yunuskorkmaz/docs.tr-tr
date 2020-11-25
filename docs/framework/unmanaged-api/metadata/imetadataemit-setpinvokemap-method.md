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
ms.openlocfilehash: 236fc848087f64c2327c2c9e790065cc3f64dc58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704311"
---
# <a name="imetadataemitsetpinvokemap-method"></a>IMetaDataEmit::SetPinvokeMap Yöntemi

Bir yöntemin PInvoke imzasının, [ımetadatayay::D Efinepınvokemap](imetadataemit-definepinvokemap-method.md)'e yönelik önceki bir çağrı tarafından tanımlanan özellikleri ayarlar veya değiştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki `mdToken` Eşleme bilgileri geçerli.  
  
 `dwMappingFlags`  
 'ndaki PInvoke tarafından eşlemeyi yapmak için kullanılan bayraklar. Bu bir değer bit değeridir `CorPinvokeMap` .  
  
 `szImportName`  
 'ndaki Yerel DLL 'de hedef dışarı aktarmanın adı.  
  
 `mrImportDLL`  
 'ndaki `mdModuleRef` Hedef YÖNETILMEYEN dll için belirteç.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
