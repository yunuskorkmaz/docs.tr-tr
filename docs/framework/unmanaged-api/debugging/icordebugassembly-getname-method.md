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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3077e0494816a083d97839d66d06b18130e5dac8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645584"
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="7d1da-102">ICorDebugAssembly::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="7d1da-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="7d1da-103">Derlemenin adını alır bu `ICorDebugAssembly` örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d1da-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d1da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d1da-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d1da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d1da-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="7d1da-106">[in] Boyutu `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="7d1da-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7d1da-107">[out] Gerçek uzunluk adını belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7d1da-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="7d1da-108">[out] Dizisi adını depolar.</span><span class="sxs-lookup"><span data-stu-id="7d1da-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d1da-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d1da-109">Remarks</span></span>  
 <span data-ttu-id="7d1da-110">`GetName` Yöntemi derlemenin tam yolu ve dosya adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d1da-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d1da-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d1da-111">Requirements</span></span>  
 <span data-ttu-id="7d1da-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d1da-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d1da-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d1da-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d1da-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d1da-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d1da-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d1da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
