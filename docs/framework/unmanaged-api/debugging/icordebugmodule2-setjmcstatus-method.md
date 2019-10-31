---
title: ICorDebugModule2::SetJMCStatus Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: a0b70078dee88b270d8361aa9bddcb7d80df1db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129464"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="d0273-102">ICorDebugModule2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0273-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="d0273-103">Bu ICorDebugModule2 içindeki tüm sınıfların tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, `pTokens` dizisinde, zıt değere göre ayarladıkları durumlar dışında, belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d0273-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0273-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0273-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0273-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0273-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="d0273-106">'ndaki Kodun ayıklanamayacağını `true` olarak ayarlayın; Aksi takdirde, `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0273-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="d0273-107">'ndaki `pTokens` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="d0273-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="d0273-108">'ndaki Her biri JMC durumunun olarak ayarlandığı bir yönteme başvuran `mdToken` değerleri dizisi!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="d0273-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0273-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0273-109">Remarks</span></span>  
 <span data-ttu-id="d0273-110">`pTokens` dizisinde belirtilen her yöntemin JMC durumu `bIsJustMycode` değerinin tersi olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d0273-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="d0273-111">Bu modüldeki diğer tüm yöntemlerin durumu `bIsJustMycode` değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d0273-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="d0273-112">`SetJMCStatus` yöntemi Bu modüldeki önceki tüm JMC ayarlarını siler.</span><span class="sxs-lookup"><span data-stu-id="d0273-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="d0273-113">Tüm işlevler başarıyla ayarlandıysa `SetJMCStatus` yöntemi bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0273-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="d0273-114">`true` işaretlenen bazı işlevler hata ayıklanabilir değilse, bir CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0273-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0273-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0273-115">Requirements</span></span>  
 <span data-ttu-id="d0273-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0273-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0273-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0273-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0273-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d0273-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0273-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0273-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
