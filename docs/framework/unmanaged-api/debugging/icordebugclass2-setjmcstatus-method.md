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
ms.openlocfilehash: d234e01e3d47a64b9a001591ee2b61074eea8afb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403400"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="c18dc-102">ICorDebugClass2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c18dc-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="c18dc-103">Her sınıf yöntemi için yöntem kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c18dc-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c18dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c18dc-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c18dc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c18dc-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="c18dc-106">[in] Kümesine `true` yöntemi kullanıcı tanımlı olduğunu belirtmek için; Aksi takdirde kümesine kodu `false`.</span><span class="sxs-lookup"><span data-stu-id="c18dc-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c18dc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c18dc-107">Remarks</span></span>  
 <span data-ttu-id="c18dc-108">Yalnızca-my-code (JMC) Adımlayıcı kullanıcı tanımlı olmayan kod atlar.</span><span class="sxs-lookup"><span data-stu-id="c18dc-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="c18dc-109">Kullanıcı tanımlı kod bir alt kümesini debuggable kodu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c18dc-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="c18dc-110">`SetJMCStatus` başarıyla diğer tüm yöntemleri için değeri ayarlar olsa bile herhangi bir yöntem değerini ayarlamak başarısız olursa S_FALSE HRESULT değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c18dc-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c18dc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c18dc-111">Requirements</span></span>  
 <span data-ttu-id="c18dc-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c18dc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c18dc-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c18dc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c18dc-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c18dc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c18dc-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c18dc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
