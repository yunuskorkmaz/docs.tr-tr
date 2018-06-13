---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0023b8ad815b9204ed56791698c7242dfe90bec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421664"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="3c735-102">ICorDebugValue::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="3c735-102">ICorDebugValue::GetSize Method</span></span>
<span data-ttu-id="3c735-103">Bu "ICorDebugValue" nesne bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="3c735-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c735-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c735-104">Syntax</span></span>  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c735-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c735-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="3c735-106">[out] Bu değer nesnesinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="3c735-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c735-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c735-107">Remarks</span></span>  
 <span data-ttu-id="3c735-108">Değer türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçi boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3c735-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="3c735-109">`ICorDebugValue::GetSize` Yöntemi döndürür `COR_E_OVERFLOW` 64 bit platformlarda 4 GB'den büyük nesneler için.</span><span class="sxs-lookup"><span data-stu-id="3c735-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="3c735-110">Kullanım [Icordebugvalue3::getsize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemi yerine nesneler için 4 GB'den büyük.</span><span class="sxs-lookup"><span data-stu-id="3c735-110">Use the [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c735-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c735-111">Requirements</span></span>  
 <span data-ttu-id="3c735-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c735-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c735-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c735-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c735-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c735-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c735-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c735-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c735-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c735-116">See Also</span></span>  
    
 [<span data-ttu-id="3c735-117">GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c735-117">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
