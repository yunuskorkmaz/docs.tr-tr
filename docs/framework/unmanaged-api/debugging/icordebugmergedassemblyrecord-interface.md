---
title: ICorDebugMergedAssemblyRecord Arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 6d5d862110cd91e8ac81c96e50486be10c579903
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793063"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="c12c5-102">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c12c5-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="c12c5-103">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c12c5-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c12c5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c12c5-104">Methods</span></span>  
  
|<span data-ttu-id="c12c5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c12c5-105">Method</span></span>|<span data-ttu-id="c12c5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c12c5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c12c5-107">GetCulture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c12c5-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="c12c5-108">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="c12c5-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="c12c5-109">GetIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c12c5-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="c12c5-110">Derlemenin önek dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="c12c5-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="c12c5-111">GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c12c5-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="c12c5-112">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="c12c5-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="c12c5-113">GetPublicKeyToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c12c5-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="c12c5-114">Derlemenin ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="c12c5-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="c12c5-115">GetSimpleName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c12c5-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="c12c5-116">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="c12c5-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="c12c5-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c12c5-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="c12c5-118">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="c12c5-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c12c5-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c12c5-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c12c5-120">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c12c5-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="c12c5-121">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="c12c5-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c12c5-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c12c5-122">Requirements</span></span>  
 <span data-ttu-id="c12c5-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c12c5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c12c5-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c12c5-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c12c5-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c12c5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c12c5-126">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c12c5-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c12c5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c12c5-127">See also</span></span>

- [<span data-ttu-id="c12c5-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c12c5-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c12c5-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c12c5-129">Debugging</span></span>](index.md)
