---
title: ICorDebugModule::GetName Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7f62385031967c164915fd31735a6d962f557fa
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894993"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="0cc3a-102">ICorDebugModule::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="0cc3a-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="0cc3a-103">Modülün dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cc3a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cc3a-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cc3a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cc3a-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="0cc3a-106">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0cc3a-107">'ndaki Döndürülen adın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="0cc3a-108">dışı Döndürülen adı depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cc3a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cc3a-109">Remarks</span></span>  
 <span data-ttu-id="0cc3a-110">Modülün dosya adı diskteki adıyla eşleşiyorsa, yöntemibirS_OKHRESULTdöndürür.`GetName`</span><span class="sxs-lookup"><span data-stu-id="0cc3a-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="0cc3a-111">`GetName`ad, dinamik veya bellek içi bir modül gibi olursa, bir S_FALSE HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cc3a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cc3a-112">Requirements</span></span>  
 <span data-ttu-id="0cc3a-113">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cc3a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cc3a-114">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0cc3a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cc3a-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0cc3a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cc3a-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cc3a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc3a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cc3a-117">See also</span></span>
