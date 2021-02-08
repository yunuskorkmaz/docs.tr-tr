---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugModule2:: SetJMCStatus yöntemi'
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
ms.openlocfilehash: 7d91d098c21eac39d18a0aa7c3d4fd795be509ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790808"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="cb295-103">ICorDebugModule2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb295-103">ICorDebugModule2::SetJMCStatus Method</span></span>

<span data-ttu-id="cb295-104">Bu ICorDebugModule2 içindeki tüm sınıfların tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, dizide yer alan ve ters değere göre ayarlanır hariç, belirtilen değere ayarlar `pTokens` .</span><span class="sxs-lookup"><span data-stu-id="cb295-104">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb295-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb295-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb295-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb295-106">Parameters</span></span>  

 `bIsJustMycode`  
 <span data-ttu-id="cb295-107">'ndaki `true` Kodun ayıklanamayacağını ise olarak ayarlayın; Aksi takdirde, olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="cb295-107">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="cb295-108">'ndaki `pTokens` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="cb295-108">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="cb295-109">'ndaki `mdToken` Her biri JMC durumunun! olarak ayarlandığı bir yönteme başvuran bir değer dizisi `bIsJustMycode` .</span><span class="sxs-lookup"><span data-stu-id="cb295-109">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb295-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb295-110">Remarks</span></span>  

 <span data-ttu-id="cb295-111">Dizide belirtilen her yöntemin JMC durumu `pTokens` değerin tersi olarak ayarlanır `bIsJustMycode` .</span><span class="sxs-lookup"><span data-stu-id="cb295-111">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="cb295-112">Bu modüldeki diğer tüm yöntemlerin durumu `bIsJustMycode` değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cb295-112">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="cb295-113">`SetJMCStatus`Yöntemi Bu modüldeki önceki tüm JMC ayarlarını siler.</span><span class="sxs-lookup"><span data-stu-id="cb295-113">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="cb295-114">`SetJMCStatus`Tüm işlevler başarıyla ayarlandıysa yöntem S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb295-114">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="cb295-115">İşaretlenen bazı işlevler hata ayıklanabilir değilse bir HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="cb295-115">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb295-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb295-116">Requirements</span></span>  

 <span data-ttu-id="cb295-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb295-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb295-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb295-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb295-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cb295-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb295-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb295-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
