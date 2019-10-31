---
title: ICorDebugFunction2::EnumerateNativeCode Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
ms.openlocfilehash: d5b24ee02a682b38dcf0cb3449f0dff197e91bf9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137824"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a>ICorDebugFunction2::EnumerateNativeCode Yöntemi
Bu ICorDebugFunction2 nesnesinin başvurduğu işlevdeki yerel kod deyimlerini içeren bir ICorDebugCodeEnum nesnesine bir arabirim işaretçisi alır.  
  
> [!NOTE]
> `EnumerateNativeCode`, .NET Framework geçerli sürümünde uygulanmıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h
