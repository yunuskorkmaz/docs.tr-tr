---
title: ICorDebugMergedAssemblyRecord Arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 721f6c1cf468b3b518d2ea213588ae2410249690
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208726"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="f9b68-102">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9b68-102">ICorDebugMergedAssemblyRecord Interface</span></span>
<span data-ttu-id="f9b68-103">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9b68-103">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9b68-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f9b68-104">Methods</span></span>  
  
|<span data-ttu-id="f9b68-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f9b68-105">Method</span></span>|<span data-ttu-id="f9b68-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9b68-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9b68-107">GetCulture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9b68-107">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="f9b68-108">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="f9b68-108">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="f9b68-109">GetIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9b68-109">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="f9b68-110">Derlemenin önek dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="f9b68-110">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="f9b68-111">GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9b68-111">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="f9b68-112">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="f9b68-112">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="f9b68-113">GetPublicKeyToken Metodu</span><span class="sxs-lookup"><span data-stu-id="f9b68-113">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="f9b68-114">Derlemenin ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="f9b68-114">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="f9b68-115">GetSimpleName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9b68-115">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="f9b68-116">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="f9b68-116">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="f9b68-117">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9b68-117">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="f9b68-118">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="f9b68-118">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9b68-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9b68-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9b68-120">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9b68-120">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f9b68-121">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f9b68-121">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b68-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9b68-122">Requirements</span></span>  
 <span data-ttu-id="f9b68-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9b68-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9b68-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f9b68-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9b68-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f9b68-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9b68-126">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9b68-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b68-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9b68-127">See also</span></span>

- [<span data-ttu-id="f9b68-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f9b68-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f9b68-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f9b68-129">Debugging</span></span>](index.md)
