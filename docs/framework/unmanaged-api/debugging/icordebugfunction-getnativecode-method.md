---
title: ICorDebugFunction::GetNativeCode Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1cb073c1f93c6d60d86e5160dcfb0cbdaf1cd33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414577"
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode Metodu
Bu ICorDebugFunction örneği tarafından temsil edilen işlevi için yerel kodu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppCode`  
 [out] Bu işlev yalnızca derlenmiş zamanında (JIT) yapılmamış Microsoft Ara dili (MSIL) kodu ise bu işlev veya null, yerel kodunu temsil eden Icordebugcode örneği için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa bu tarafından temsil edilen işlevi `ICorDebugFunction` örneği açıldı JIT derlenmiş birden fazla kez Genel türleri gibi söz konusu olduğunda `GetNativeCode` bir rastgele yerel kod nesnesi döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
