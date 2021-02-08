---
description: ': ICorDebugLoadedModule arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugLoadedModule Arabirimi
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 6a1b466a9d2d7781fad7ac2bc8c24f0b2a5c23e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801234"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="b58b4-103">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b58b4-103">ICorDebugLoadedModule Interface</span></span>

<span data-ttu-id="b58b4-104">Yüklü bir modül hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b58b4-104">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b58b4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b58b4-105">Methods</span></span>  
  
|<span data-ttu-id="b58b4-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b58b4-106">Method</span></span>|<span data-ttu-id="b58b4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b58b4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b58b4-108">GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b58b4-108">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="b58b4-109">Yüklenen modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="b58b4-109">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="b58b4-110">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b58b4-110">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="b58b4-111">Yüklenen modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="b58b4-111">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="b58b4-112">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b58b4-112">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="b58b4-113">Yüklenen modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="b58b4-113">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b58b4-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b58b4-114">Remarks</span></span>  

 <span data-ttu-id="b58b4-115">`ICorDebugLoadedModule`Arabirim bir hata ayıklayıcı tarafından uygulanır ve hata ayıklayıcıdan yüklenen modül hakkında bilgi almak IÇIN clr hata ayıklama arabirimleri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b58b4-115">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b58b4-116">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b58b4-116">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b58b4-117">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="b58b4-117">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b58b4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b58b4-118">Requirements</span></span>  

 <span data-ttu-id="b58b4-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b58b4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b58b4-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b58b4-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b58b4-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b58b4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b58b4-122">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b58b4-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58b4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b58b4-123">See also</span></span>

- [<span data-ttu-id="b58b4-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b58b4-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b58b4-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b58b4-125">Debugging</span></span>](index.md)
