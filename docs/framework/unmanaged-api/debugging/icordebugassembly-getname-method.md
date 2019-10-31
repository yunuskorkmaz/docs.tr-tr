---
title: ICorDebugAssembly::GetName Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
ms.openlocfilehash: 5e3619d12b9377a8482254703d3d97d0348a013b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127165"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="88ae2-102">ICorDebugAssembly::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="88ae2-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="88ae2-103">Bu `ICorDebugAssembly` örneğinin temsil ettiği derlemenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="88ae2-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88ae2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88ae2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88ae2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88ae2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="88ae2-106">'ndaki `szName` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="88ae2-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="88ae2-107">dışı Adın gerçek uzunluğunu belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="88ae2-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="88ae2-108">dışı Adı depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="88ae2-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88ae2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88ae2-109">Remarks</span></span>  
 <span data-ttu-id="88ae2-110">`GetName` yöntemi, derlemenin tam yolunu ve dosya adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="88ae2-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88ae2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88ae2-111">Requirements</span></span>  
 <span data-ttu-id="88ae2-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88ae2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88ae2-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="88ae2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88ae2-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="88ae2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88ae2-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88ae2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
