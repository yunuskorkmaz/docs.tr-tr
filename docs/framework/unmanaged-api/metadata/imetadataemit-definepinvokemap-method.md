---
title: IMetaDataEmit::DefinePinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: 447ec44ed3efc4eec84d1e4acd6f2ec1a730bf74
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008033"
---
# <a name="imetadataemitdefinepinvokemap-method"></a>IMetaDataEmit::DefinePinvokeMap Yöntemi
Belirtilen belirteç tarafından başvurulan metodun PInvoke imzasının özelliklerini ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `tk`  
 'ndaki Hedef yöntemi için belirteç.  
  
 `dwMappingFlags`  
 'ndaki PInvoke tarafından eşlemeyi yapmak için kullanılan bayraklar.  
  
 `szImportName`  
 'ndaki Yönetilmeyen DLL içindeki hedef dışarı aktarma yönteminin adı.  
  
 `mrImportDLL`  
 'ndaki Hedef yerel DLL için belirteç.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
