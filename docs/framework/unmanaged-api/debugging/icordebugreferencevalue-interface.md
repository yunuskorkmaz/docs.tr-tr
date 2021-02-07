---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugReferenceValue arabirimi'
title: ICorDebugReferenceValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: e516b1178b4f4268472dedd37d6443e673e16af6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690970"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="f0de5-103">ICorDebugReferenceValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0de5-103">ICorDebugReferenceValue Interface</span></span>

<span data-ttu-id="f0de5-104">Bir nesne başvurusu olan bir değeri yöneten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0de5-104">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="f0de5-105">(Diğer bir deyişle, bu arabirim bir işaretçiyi yöneten yöntemler sağlar.) Bu arabirim "ICorDebugValue" uygular.</span><span class="sxs-lookup"><span data-stu-id="f0de5-105">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0de5-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f0de5-106">Methods</span></span>  
  
|<span data-ttu-id="f0de5-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f0de5-107">Method</span></span>|<span data-ttu-id="f0de5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0de5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0de5-109">Dereference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0de5-109">Dereference Method</span></span>](icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="f0de5-110">Başvurulan nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="f0de5-110">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="f0de5-111">DereferenceStrong Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0de5-111">DereferenceStrong Method</span></span>](icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="f0de5-112">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="f0de5-112">Not implemented.</span></span> <span data-ttu-id="f0de5-113">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="f0de5-113">Do not call this method.</span></span>|  
|[<span data-ttu-id="f0de5-114">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0de5-114">GetValue Method</span></span>](icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="f0de5-115">Başvurulan nesnenin geçerli bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="f0de5-115">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="f0de5-116">IsNull Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0de5-116">IsNull Method</span></span>](icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="f0de5-117">Bunun null bir değer olup olmadığını belirten bir değer alır `ICorDebugReferenceValue` , bu durumda `ICorDebugReferenceValue` bir nesneyi işaret etmez.</span><span class="sxs-lookup"><span data-stu-id="f0de5-117">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="f0de5-118">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0de5-118">SetValue Method</span></span>](icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="f0de5-119">Geçerli bellek adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0de5-119">Sets the current memory address.</span></span> <span data-ttu-id="f0de5-120">Diğer bir deyişle, bu yöntem bunu `ICorDebugReferenceValue` bir nesnesine işaret etmek üzere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0de5-120">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0de5-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0de5-121">Remarks</span></span>  

 <span data-ttu-id="f0de5-122">Ortak dil çalışma zamanı (CLR), hata ayıklama işlemi devam eden nesneler üzerinde çöp toplama işlemi yapamayabilir.</span><span class="sxs-lookup"><span data-stu-id="f0de5-122">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="f0de5-123">Çöp toplama, nesneleri belleğin etrafında taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="f0de5-123">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="f0de5-124">, `ICorDebugReferenceValue` Bilgileri çöp toplamadan sonra güncelleştirilmesini sağlamak için çöp koleksiyonuyla birlikte çalışır veya çöp toplamadan önce örtülü olarak geçersiz kılınacaktır.</span><span class="sxs-lookup"><span data-stu-id="f0de5-124">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="f0de5-125">`ICorDebugReferenceValue`Hata ayıklama işlemi devam ettikten sonra nesne örtük olarak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="f0de5-125">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="f0de5-126">Türetilmiş "ıcorıı Ghandlevalue", açık veya kullanıma sunuluncaya kadar geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="f0de5-126">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0de5-127">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f0de5-127">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0de5-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0de5-128">Requirements</span></span>  

 <span data-ttu-id="f0de5-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0de5-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0de5-130">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0de5-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0de5-131">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f0de5-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0de5-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0de5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0de5-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0de5-133">See also</span></span>

- [<span data-ttu-id="f0de5-134">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f0de5-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
