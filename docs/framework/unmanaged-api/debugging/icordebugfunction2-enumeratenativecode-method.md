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
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="ce588-102">ICorDebugFunction2::EnumerateNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce588-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="ce588-103">Bu ICorDebugFunction2 nesnesinin başvurduğu işlevdeki yerel kod deyimlerini içeren bir ICorDebugCodeEnum nesnesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ce588-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce588-104">`EnumerateNativeCode`, .NET Framework geçerli sürümünde uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="ce588-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce588-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce588-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ce588-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce588-106">Requirements</span></span>  
 <span data-ttu-id="ce588-107">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ce588-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
