---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugAppDomainEnum:: Next yöntemi'
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
ms.openlocfilehash: ac5397250e661b4ed380b3272744957f86e1a07b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791536"
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="03c30-103">ICorDebugAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03c30-103">ICorDebugAppDomainEnum::Next Method</span></span>

<span data-ttu-id="03c30-104">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen sayıda uygulama etki alanı alır.</span><span class="sxs-lookup"><span data-stu-id="03c30-104">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03c30-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03c30-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03c30-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03c30-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="03c30-107">'ndaki Alınacak uygulama etki alanlarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="03c30-107">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="03c30-108">dışı Her biri bir uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="03c30-108">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="03c30-109">dışı Aslında döndürülen uygulama etki alanlarının sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03c30-109">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="03c30-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="03c30-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03c30-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03c30-111">Requirements</span></span>  

 <span data-ttu-id="03c30-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03c30-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03c30-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="03c30-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03c30-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="03c30-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03c30-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03c30-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
