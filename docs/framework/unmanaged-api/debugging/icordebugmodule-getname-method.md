---
description: ': ICorDebugModule:: GetName metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0f81271b2be283621027f4c835b6f220a383d771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660219"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="73fa2-103">ICorDebugModule::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="73fa2-103">ICorDebugModule::GetName Method</span></span>

<span data-ttu-id="73fa2-104">Modülün dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="73fa2-104">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73fa2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73fa2-105">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73fa2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73fa2-106">Parameters</span></span>  

 `cchname`  
 <span data-ttu-id="73fa2-107">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="73fa2-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="73fa2-108">'ndaki Döndürülen adın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="73fa2-108">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="73fa2-109">dışı Döndürülen adı depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="73fa2-109">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73fa2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73fa2-110">Remarks</span></span>  

 <span data-ttu-id="73fa2-111">`GetName`Modülün dosya adı diskteki adla eşleşiyorsa Yöntem bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="73fa2-111">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="73fa2-112">`GetName` ad, dinamik veya bellek içi bir modül için gibi, varsa HRESULT S_FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="73fa2-112">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73fa2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73fa2-113">Requirements</span></span>  

 <span data-ttu-id="73fa2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73fa2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73fa2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73fa2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73fa2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="73fa2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73fa2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73fa2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fa2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73fa2-118">See also</span></span>
