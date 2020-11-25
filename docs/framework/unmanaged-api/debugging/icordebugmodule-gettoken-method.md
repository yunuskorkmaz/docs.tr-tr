---
title: ICorDebugModule::GetToken Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
ms.openlocfilehash: 6ffc74247a4ecafcc3744923c0def99220b5ca6f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709888"
---
# <a name="icordebugmodulegettoken-method"></a>ICorDebugModule::GetToken Yöntemi

Bu modül için tablo girişi belirtecini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pToken`  
 dışı `mdModule` Modülün meta verilerine başvuran belirtece yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Belirteç [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md)ve [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) meta veri alma arabirimlerine geçirilebilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta veri](../metadata/index.md)
