---
title: ICorPublishAppDomainEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
ms.openlocfilehash: 6f7f400c51ded0b98c0c2286cb6f90bbd77e47d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178393"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="5bc61-102">ICorPublishAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bc61-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="5bc61-103">Geçerli konumdan başlayarak, şu anda işlemde bulunan belirtilen uygulama etki alanı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5bc61-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bc61-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc61-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bc61-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5bc61-106">[içinde] Alınacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="5bc61-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="5bc61-107">[çıkış] Her biri bir uygulama etki alanını temsil eden, alınan [ICorPublishAppDomain](icorpublishappdomain-interface.md) nesnelerinin dizine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5bc61-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5bc61-108">[çıkış] Gerçekte döndürülen uygulama etki alanlarının sayısına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5bc61-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="5bc61-109">Bu değer, varsa `celt` null olabilir.</span><span class="sxs-lookup"><span data-stu-id="5bc61-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc61-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bc61-110">Requirements</span></span>  
 <span data-ttu-id="5bc61-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc61-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc61-112">**Üstbilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5bc61-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5bc61-113">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bc61-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bc61-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc61-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc61-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bc61-115">See also</span></span>

- [<span data-ttu-id="5bc61-116">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bc61-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
