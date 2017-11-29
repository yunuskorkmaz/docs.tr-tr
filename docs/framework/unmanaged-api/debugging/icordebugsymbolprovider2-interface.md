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
ms.openlocfilehash: 5ff0446ba8646620cb7322f74a81769e41f35b0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="8a3e5-102">ICorDebugSymbolProvider2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a3e5-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="8a3e5-103">Mantıksal olarak genişletir [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) ek hata ayıklama sembol bilgilerini almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="8a3e5-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a3e5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a3e5-104">Methods</span></span>  
  
|<span data-ttu-id="8a3e5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8a3e5-105">Method</span></span>|<span data-ttu-id="8a3e5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a3e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a3e5-107">GetFrameProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a3e5-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="8a3e5-108">Bir yöntem ve bir kod göreli sanal adres verilen üst çerçeve göreli sanal adres başlatma yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a3e5-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="8a3e5-109">GetGenericDictionaryInfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a3e5-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="8a3e5-110">Genel bir sözlük harita alır.</span><span class="sxs-lookup"><span data-stu-id="8a3e5-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a3e5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a3e5-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a3e5-112">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a3e5-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8a3e5-113">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="8a3e5-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a3e5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a3e5-114">Requirements</span></span>  
 <span data-ttu-id="8a3e5-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a3e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a3e5-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a3e5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a3e5-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a3e5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a3e5-118">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a3e5-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3e5-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a3e5-119">See Also</span></span>  
 [<span data-ttu-id="8a3e5-120">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a3e5-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="8a3e5-121">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a3e5-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8a3e5-122">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8a3e5-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
