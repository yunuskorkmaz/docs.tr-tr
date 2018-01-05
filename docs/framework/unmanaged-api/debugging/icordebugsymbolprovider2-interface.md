---
title: ICorDebugSymbolProvider2 arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7666b8d64b689d3640594f07614be97b72e85a8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="7bd94-102">ICorDebugSymbolProvider2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bd94-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="7bd94-103">Mantıksal olarak genişletir [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) ek hata ayıklama sembol bilgilerini almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="7bd94-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7bd94-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7bd94-104">Methods</span></span>  
  
|<span data-ttu-id="7bd94-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7bd94-105">Method</span></span>|<span data-ttu-id="7bd94-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bd94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7bd94-107">GetFrameProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7bd94-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="7bd94-108">Bir yöntem ve bir kod göreli sanal adres verilen üst çerçeve göreli sanal adres başlatma yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bd94-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="7bd94-109">GetGenericDictionaryInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7bd94-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="7bd94-110">Genel bir sözlük harita alır.</span><span class="sxs-lookup"><span data-stu-id="7bd94-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bd94-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bd94-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bd94-112">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bd94-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7bd94-113">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="7bd94-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bd94-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bd94-114">Requirements</span></span>  
 <span data-ttu-id="7bd94-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bd94-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bd94-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bd94-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bd94-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bd94-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bd94-118">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bd94-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd94-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bd94-119">See Also</span></span>  
 [<span data-ttu-id="7bd94-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bd94-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="7bd94-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7bd94-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7bd94-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7bd94-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
