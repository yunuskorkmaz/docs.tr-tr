---
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
ms.openlocfilehash: 16d7b89ee441e8d634c36fb87185b3f2846860b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137717"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="a3e61-102">ICorDebugReferenceValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3e61-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="a3e61-103">Bir nesne başvurusu olan bir değeri yöneten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3e61-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="a3e61-104">(Diğer bir deyişle, bu arabirim bir işaretçiyi yöneten yöntemler sağlar.) Bu arabirim "ICorDebugValue" uygular.</span><span class="sxs-lookup"><span data-stu-id="a3e61-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3e61-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a3e61-105">Methods</span></span>  
  
|<span data-ttu-id="a3e61-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a3e61-106">Method</span></span>|<span data-ttu-id="a3e61-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3e61-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3e61-108">Dereference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3e61-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="a3e61-109">Başvurulan nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="a3e61-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="a3e61-110">DereferenceStrong Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3e61-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="a3e61-111">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="a3e61-111">Not implemented.</span></span> <span data-ttu-id="a3e61-112">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="a3e61-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="a3e61-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3e61-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="a3e61-114">Başvurulan nesnenin geçerli bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="a3e61-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="a3e61-115">IsNull Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3e61-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="a3e61-116">Bu `ICorDebugReferenceValue` null bir değer olup olmadığını belirten bir değer alır, bu durumda `ICorDebugReferenceValue` bir nesneyi işaret etmez.</span><span class="sxs-lookup"><span data-stu-id="a3e61-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="a3e61-117">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3e61-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="a3e61-118">Geçerli bellek adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a3e61-118">Sets the current memory address.</span></span> <span data-ttu-id="a3e61-119">Diğer bir deyişle, bu yöntem bir nesneyi işaret etmek için bu `ICorDebugReferenceValue` ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a3e61-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3e61-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3e61-120">Remarks</span></span>  
 <span data-ttu-id="a3e61-121">Ortak dil çalışma zamanı (CLR), hata ayıklama işlemi devam eden nesneler üzerinde çöp toplama işlemi yapamayabilir.</span><span class="sxs-lookup"><span data-stu-id="a3e61-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="a3e61-122">Çöp toplama, nesneleri belleğin etrafında taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="a3e61-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="a3e61-123">`ICorDebugReferenceValue`, çöp toplamadan sonra bilgileri güncelleştirilebilmeleri için çöp koleksiyonuyla birlikte çalışır veya çöp toplamadan önce örtük olarak geçersiz kılınacaktır.</span><span class="sxs-lookup"><span data-stu-id="a3e61-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="a3e61-124">Hata ayıklama işlemi devam ettikten sonra `ICorDebugReferenceValue` nesnesi örtük olarak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="a3e61-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="a3e61-125">Türetilmiş "ıcorıı Ghandlevalue", açık veya kullanıma sunuluncaya kadar geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="a3e61-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3e61-126">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a3e61-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3e61-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3e61-127">Requirements</span></span>  
 <span data-ttu-id="a3e61-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3e61-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3e61-129">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3e61-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3e61-130">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3e61-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3e61-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3e61-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3e61-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3e61-132">See also</span></span>

- [<span data-ttu-id="a3e61-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a3e61-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
