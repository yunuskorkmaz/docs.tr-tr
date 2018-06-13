---
title: ICorDebugSymbolProvider2 arabirimi
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7db1bba48f4685338f4531e2c11506de338e5c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423227"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="4d8ed-102">ICorDebugSymbolProvider2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d8ed-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="4d8ed-103">Mantıksal olarak genişletir [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) ek hata ayıklama sembol bilgilerini almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="4d8ed-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d8ed-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4d8ed-104">Methods</span></span>  
  
|<span data-ttu-id="4d8ed-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4d8ed-105">Method</span></span>|<span data-ttu-id="4d8ed-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d8ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d8ed-107">GetFrameProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d8ed-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="4d8ed-108">Bir yöntem ve bir kod göreli sanal adres verilen üst çerçeve göreli sanal adres başlatma yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d8ed-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="4d8ed-109">GetGenericDictionaryInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d8ed-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="4d8ed-110">Genel bir sözlük harita alır.</span><span class="sxs-lookup"><span data-stu-id="4d8ed-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d8ed-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d8ed-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d8ed-112">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4d8ed-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4d8ed-113">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="4d8ed-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d8ed-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d8ed-114">Requirements</span></span>  
 <span data-ttu-id="4d8ed-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d8ed-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d8ed-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d8ed-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d8ed-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d8ed-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d8ed-118">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d8ed-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8ed-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d8ed-119">See Also</span></span>  
 [<span data-ttu-id="4d8ed-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d8ed-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="4d8ed-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4d8ed-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4d8ed-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4d8ed-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
