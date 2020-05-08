---
title: ICorDebugAppDomainEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
ms.openlocfilehash: 17bf4c92b1e1347a8fe790c8df5937de0f95df4d
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895080"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="f9b29-102">ICorDebugAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9b29-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="f9b29-103">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen sayıda uygulama etki alanı alır.</span><span class="sxs-lookup"><span data-stu-id="f9b29-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9b29-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9b29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9b29-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f9b29-106">'ndaki Alınacak uygulama etki alanlarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="f9b29-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="f9b29-107">dışı Her biri bir uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="f9b29-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f9b29-108">dışı Aslında döndürülen uygulama etki alanlarının sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9b29-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="f9b29-109">Bu değer bir `celt` ise null olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9b29-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b29-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9b29-110">Requirements</span></span>  
 <span data-ttu-id="f9b29-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9b29-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9b29-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f9b29-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9b29-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f9b29-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9b29-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9b29-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
