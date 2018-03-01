---
title: ICorDebugModule::GetName Metodu
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
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64be936277b0ebe04248ae2913a882b628ee363f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="0f040-102">ICorDebugModule::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="0f040-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="0f040-103">Modül dosyası adını alır.</span><span class="sxs-lookup"><span data-stu-id="0f040-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f040-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f040-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f040-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f040-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="0f040-106">[in] Boyutunu `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="0f040-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0f040-107">[in] Döndürülen adının uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0f040-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="0f040-108">[out] Döndürülen adını depolar bir dizi.</span><span class="sxs-lookup"><span data-stu-id="0f040-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f040-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f040-109">Remarks</span></span>  
 <span data-ttu-id="0f040-110">`GetName` Yöntemi modülün dosya adı diskte adı eşleşirse S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f040-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="0f040-111">`GetName`ad yoksa üretilmiş, dinamik ya da bellek içi modülü gibi S_FALSE HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f040-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f040-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f040-112">Requirements</span></span>  
 <span data-ttu-id="0f040-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f040-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f040-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f040-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f040-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f040-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f040-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f040-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f040-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f040-117">See Also</span></span>  
    
 
