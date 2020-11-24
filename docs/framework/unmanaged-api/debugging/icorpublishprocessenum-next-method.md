---
title: ICorPublishProcessEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
ms.openlocfilehash: 9965a468f788efead0477bb7574ef3bf156fd869
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692481"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="b6527-102">ICorPublishProcessEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6527-102">ICorPublishProcessEnum::Next Method</span></span>

<span data-ttu-id="b6527-103">Geçerli imleç konumundan başlayarak koleksiyondan belirtilen işlem sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b6527-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6527-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b6527-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6527-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6527-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="b6527-106">'ndaki Alınacak işlem sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6527-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="b6527-107">dışı Her biri bir işlemi temsil eden [ICorPublishProcess](icorpublishprocess-interface.md) nesnelerinin dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6527-107">[out] A pointer to the array of retrieved [ICorPublishProcess](icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b6527-108">dışı Gerçekten döndürülen işlem sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6527-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="b6527-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="b6527-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6527-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6527-110">Requirements</span></span>  

 <span data-ttu-id="b6527-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6527-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6527-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b6527-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b6527-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b6527-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6527-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6527-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6527-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6527-115">See also</span></span>

- [<span data-ttu-id="b6527-116">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6527-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)
