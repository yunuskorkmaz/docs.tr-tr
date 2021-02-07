---
description: 'Daha fazla bilgi edinin: ICorDebugFunction2:: EnumerateNativeCode yöntemi'
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
ms.openlocfilehash: 617d6dbfdb596df192e2722a47d81517ae57ac1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692257"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="23057-103">ICorDebugFunction2::EnumerateNativeCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23057-103">ICorDebugFunction2::EnumerateNativeCode Method</span></span>

<span data-ttu-id="23057-104">Bu ICorDebugFunction2 nesnesinin başvurduğu işlevdeki yerel kod deyimlerini içeren bir ICorDebugCodeEnum nesnesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="23057-104">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23057-105">`EnumerateNativeCode` geçerli .NET Framework sürümünde uygulanmıyor.</span><span class="sxs-lookup"><span data-stu-id="23057-105">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23057-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="23057-106">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="23057-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23057-107">Requirements</span></span>  

 <span data-ttu-id="23057-108">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="23057-108">**Header:** CorDebug.idl, CorDebug.h</span></span>
