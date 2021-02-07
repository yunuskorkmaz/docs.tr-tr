---
description: ': ICorDebugValue:: GetSize yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugValue::GetSize Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3fc2582990d58fa2e42f240dfd3e563eed34e372
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690346"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="c4719-103">ICorDebugValue::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="c4719-103">ICorDebugValue::GetSize Method</span></span>

<span data-ttu-id="c4719-104">Bu "ICorDebugValue" nesnesinin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c4719-104">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4719-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4719-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4719-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4719-106">Parameters</span></span>  

 `pSize`  
 <span data-ttu-id="c4719-107">dışı Bu değer nesnesinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c4719-107">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4719-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4719-108">Remarks</span></span>  

 <span data-ttu-id="c4719-109">Değerin türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçinin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4719-109">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="c4719-110">`ICorDebugValue::GetSize`Yöntemi `COR_E_OVERFLOW` 64-bit platformlarda 4 GB 'den büyük nesneler için döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4719-110">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="c4719-111">4 GB 'den büyük nesneler için yerine [ICorDebugValue3:: GetSize64](icordebugvalue3-getsize64-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4719-111">Use the [ICorDebugValue3::GetSize64](icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4719-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4719-112">Requirements</span></span>  

 <span data-ttu-id="c4719-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4719-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4719-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4719-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4719-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4719-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4719-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4719-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4719-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4719-117">See also</span></span>

- [<span data-ttu-id="c4719-118">GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4719-118">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)
