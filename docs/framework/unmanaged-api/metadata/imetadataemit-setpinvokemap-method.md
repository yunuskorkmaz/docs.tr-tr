---
description: ': Imetadatayayma:: Setpınvokemap yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e50f06385b599a99454da0a9b971b00806d3140a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771853"
---
# <a name="imetadataemitsetpinvokemap-method"></a>IMetaDataEmit::SetPinvokeMap Yöntemi

Bir yöntemin PInvoke imzasının, [ımetadatayay::D Efinepınvokemap](imetadataemit-definepinvokemap-method.md)'e yönelik önceki bir çağrı tarafından tanımlanan özellikleri ayarlar veya değiştirir.  
  
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
