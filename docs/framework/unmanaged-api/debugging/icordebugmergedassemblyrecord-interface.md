---
description: ': Icordebugmergedassemblyrecord arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugMergedAssemblyRecord Arabirimi
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: e64c0ee30a8e8956dd336a30e6c81962c75f04e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650306"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="a7812-103">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7812-103">ICorDebugMergedAssemblyRecord Interface</span></span>

<span data-ttu-id="a7812-104">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7812-104">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7812-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a7812-105">Methods</span></span>  
  
|<span data-ttu-id="a7812-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a7812-106">Method</span></span>|<span data-ttu-id="a7812-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7812-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7812-108">GetCulture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7812-108">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="a7812-109">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="a7812-109">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="a7812-110">GetIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7812-110">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="a7812-111">Derlemenin önek dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="a7812-111">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="a7812-112">GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7812-112">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="a7812-113">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="a7812-113">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="a7812-114">GetPublicKeyToken Metodu</span><span class="sxs-lookup"><span data-stu-id="a7812-114">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="a7812-115">Derlemenin ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="a7812-115">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="a7812-116">GetSimpleName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7812-116">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="a7812-117">Derlemenin basit adını alır.</span><span class="sxs-lookup"><span data-stu-id="a7812-117">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="a7812-118">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7812-118">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="a7812-119">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="a7812-119">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7812-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7812-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7812-121">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7812-121">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a7812-122">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="a7812-122">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7812-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7812-123">Requirements</span></span>  

 <span data-ttu-id="a7812-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7812-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7812-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a7812-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7812-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7812-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7812-127">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7812-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7812-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7812-128">See also</span></span>

- [<span data-ttu-id="a7812-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a7812-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a7812-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a7812-130">Debugging</span></span>](index.md)
