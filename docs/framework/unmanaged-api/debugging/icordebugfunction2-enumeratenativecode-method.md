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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4d15d9ae63e63f98ab73e250df558dfa16002a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959971"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a>ICorDebugFunction2::EnumerateNativeCode Yöntemi
Bu Icordebugfunction2 nesne tarafından başvurulan işlevinde yerel kod deyimlerini içeren bir Icordebugcodeenum nesnesine bir arabirim işaretçisi alır.  
  
> [!NOTE]
>  `EnumerateNativeCode` .NET Framework'ün geçerli sürümde uygulanmadı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Üst bilgi:** CorDebug.idl, CorDebug.h
