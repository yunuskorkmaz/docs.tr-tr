---
title: ICorDebugClass2::SetJMCStatus Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed6570e11008e52d4b1f97c2dc90e2ccbef2e35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750624"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="c044a-102">ICorDebugClass2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c044a-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="c044a-103">Sınıfının her yöntemi için yöntem kullanıcı tarafından tanımlanan kod olup olmadığını gösteren bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c044a-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c044a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c044a-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c044a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c044a-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="c044a-106">[in] Kümesine `true` yöntemi, kullanıcı tanımlı olduğunu belirtmek için; Aksi takdirde, kümesine kodu `false`.</span><span class="sxs-lookup"><span data-stu-id="c044a-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c044a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c044a-107">Remarks</span></span>  
 <span data-ttu-id="c044a-108">Just--kendi kodum (JMC) Adımlayıcı kullanıcı tanımlı olmayan kod atlar.</span><span class="sxs-lookup"><span data-stu-id="c044a-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="c044a-109">Kullanıcı tarafından tanımlanan kod hata ayıklaması yapılabilir kod bir alt kümesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c044a-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="c044a-110">`SetJMCStatus` başarılı bir şekilde tüm diğer yöntemler için değeri ayarlar bile herhangi bir yöntem için bir değer ayarlamak başarısız olursa bir HRESULT değerini S_FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c044a-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c044a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c044a-111">Requirements</span></span>  
 <span data-ttu-id="c044a-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c044a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c044a-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c044a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c044a-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c044a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c044a-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c044a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
