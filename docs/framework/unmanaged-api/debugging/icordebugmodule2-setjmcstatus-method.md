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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d438123dcefb901098954845596c210e5b76cea6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764107"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="cd2fc-102">ICorDebugModule2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd2fc-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="cd2fc-103">Tüm sınıfların tüm yöntemleri yalnızca benim kodum (JMC) durumunu bu Icordebugmodule2 hariç belirtilen değere ayarlar `pTokens` dizisi karşı değer olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd2fc-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd2fc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd2fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd2fc-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="cd2fc-106">[in] Kümesine `true` kod hata ayıklaması; tersi durumda ise, kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="cd2fc-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="cd2fc-107">[in] Boyutu `pTokens` dizisi.</span><span class="sxs-lookup"><span data-stu-id="cd2fc-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="cd2fc-108">[in] Bir dizi `mdToken` değerler, her biri JMC durumunu kümesine sahip olan bir yönteme başvuran!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="cd2fc-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd2fc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd2fc-109">Remarks</span></span>  
 <span data-ttu-id="cd2fc-110">Belirtilen her yöntemin JMC durumunu `pTokens` dizi tersini için ayarlanmış `bIsJustMycode` değeri.</span><span class="sxs-lookup"><span data-stu-id="cd2fc-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="cd2fc-111">Bu modüldeki tüm diğer yöntemler durumunu ayarlamak `bIsJustMycode` değeri.</span><span class="sxs-lookup"><span data-stu-id="cd2fc-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="cd2fc-112">`SetJMCStatus` Yöntemi bu modüldeki tüm önceki JMC ayarları siler.</span><span class="sxs-lookup"><span data-stu-id="cd2fc-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="cd2fc-113">`SetJMCStatus` Yöntemi, tüm işlevler başarıyla belirlenmişse bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd2fc-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="cd2fc-114">CORDBG_E_FUNCTION_NOT_DEBUGGABLE bazı işlevler, HRESULT işaretlenir döndürür `true` hata ayıklanabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="cd2fc-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd2fc-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd2fc-115">Requirements</span></span>  
 <span data-ttu-id="cd2fc-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd2fc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd2fc-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd2fc-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd2fc-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd2fc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd2fc-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd2fc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
