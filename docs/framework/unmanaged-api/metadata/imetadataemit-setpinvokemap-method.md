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
ms.openlocfilehash: 0d34c7a2992a2779b96ec87f1a0175d8fcbce34a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007799"
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
 'ndaki `mdToken`Eşleme bilgileri geçerli.  
  
 `dwMappingFlags`  
 'ndaki PInvoke tarafından eşlemeyi yapmak için kullanılan bayraklar. Bu bir değer bit değeridir `CorPinvokeMap` .  
  
 `szImportName`  
 'ndaki Yerel DLL 'de hedef dışarı aktarmanın adı.  
  
 `mrImportDLL`  
 'ndaki `mdModuleRef`Hedef YÖNETILMEYEN dll için belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
