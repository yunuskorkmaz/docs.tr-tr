---
title: "ICorDebugModule2::SetJMCStatus Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a461a9c05b18de45426247743c6e4ffca775025a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="1fb6e-102">ICorDebugModule2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1fb6e-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="1fb6e-103">Bu Icordebugmodule2 belirtilen değerle hariç tüm sınıfların tüm yöntemleri yalnızca My kod (JMC) durumunu ayarlar `pTokens` ters değerine ayarlar dizi.</span><span class="sxs-lookup"><span data-stu-id="1fb6e-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1fb6e-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fb6e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1fb6e-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="1fb6e-106">[in] Kümesine `true` kod hata ayıklaması; tersi durumda ise, kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="1fb6e-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="1fb6e-107">[in] Boyutunu `pTokens` dizi.</span><span class="sxs-lookup"><span data-stu-id="1fb6e-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="1fb6e-108">[in] Bir dizi `mdToken` değerleri, her biri başvurduğu JMC durumunu kümesine sahip bir yöntem!`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="1fb6e-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fb6e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1fb6e-109">Remarks</span></span>  
 <span data-ttu-id="1fb6e-110">Belirtilen her yöntemi JMC durumunu `pTokens` dizi karşıtı için ayarlanmış `bIsJustMycode` değeri.</span><span class="sxs-lookup"><span data-stu-id="1fb6e-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="1fb6e-111">Bu modüldeki tüm diğer yöntemleri durumunu ayarlamak `bIsJustMycode` değeri.</span><span class="sxs-lookup"><span data-stu-id="1fb6e-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="1fb6e-112">`SetJMCStatus` Yöntemi bu modüldeki tüm önceki JMC ayarlarını siler.</span><span class="sxs-lookup"><span data-stu-id="1fb6e-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="1fb6e-113">`SetJMCStatus` Yöntemi hatalı döndürürse S_OK HRESULT tüm işlevleri başarıyla ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="1fb6e-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="1fb6e-114">CORDBG_E_FUNCTION_NOT_DEBUGGABLE bazı çalışırsa, HRESULT işaretlenir döndürür `true` debuggable değildir.</span><span class="sxs-lookup"><span data-stu-id="1fb6e-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fb6e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fb6e-115">Requirements</span></span>  
 <span data-ttu-id="1fb6e-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fb6e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fb6e-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1fb6e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1fb6e-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fb6e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fb6e-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fb6e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
