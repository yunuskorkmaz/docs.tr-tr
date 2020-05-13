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
ms.openlocfilehash: 55342c803756aa10c2e7c835d9e1d58b439bb36c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212548"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="7e978-102">ICorDebugModule::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="7e978-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="7e978-103">Modülün dosya adını alır.</span><span class="sxs-lookup"><span data-stu-id="7e978-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e978-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e978-104">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e978-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e978-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="7e978-106">'ndaki `szName`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="7e978-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7e978-107">'ndaki Döndürülen adın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7e978-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="7e978-108">dışı Döndürülen adı depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="7e978-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e978-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e978-109">Remarks</span></span>  
 <span data-ttu-id="7e978-110">`GetName`Modülün dosya adı diskteki adla eşleşiyorsa Yöntem bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e978-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="7e978-111">`GetName`ad, dinamik veya bellek içi bir modül için gibi, varsa HRESULT S_FALSE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e978-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e978-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e978-112">Requirements</span></span>  
 <span data-ttu-id="7e978-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e978-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e978-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7e978-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e978-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7e978-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e978-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e978-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e978-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e978-117">See also</span></span>
