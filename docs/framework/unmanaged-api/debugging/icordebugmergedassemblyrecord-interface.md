---
title: ICorDebugMergedAssemblyRecord Arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: a26702c6b21e4bfe352d861387a80b976a8dc556
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710499"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="55955-102">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55955-102">ICorDebugMergedAssemblyRecord Interface</span></span>

<span data-ttu-id="55955-103">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="55955-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55955-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="55955-104">Methods</span></span>  
  
|<span data-ttu-id="55955-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="55955-105">Method</span></span>|<span data-ttu-id="55955-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55955-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55955-107">GetCulture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55955-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="55955-108">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="55955-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="55955-109">GetIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55955-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="55955-110">Derlemenin önek dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="55955-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="55955-111">GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55955-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="55955-112">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="55955-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="55955-113">GetPublicKeyToken Metodu</span><span class="sxs-lookup"><span data-stu-id="55955-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="55955-114">Derlemenin ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="55955-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="55955-115">GetSimpleName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55955-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="55955-116">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="55955-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="55955-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55955-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="55955-118">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="55955-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55955-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55955-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55955-120">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55955-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="55955-121">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="55955-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55955-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55955-122">Requirements</span></span>  

 <span data-ttu-id="55955-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55955-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55955-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="55955-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55955-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="55955-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55955-126">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55955-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55955-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55955-127">See also</span></span>

- [<span data-ttu-id="55955-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="55955-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="55955-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="55955-129">Debugging</span></span>](index.md)
