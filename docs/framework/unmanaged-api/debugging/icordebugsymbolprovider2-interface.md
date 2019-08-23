---
title: ICorDebugSymbolProvider2 Arabirimi
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 587fc29edce72edca7c811c737d67d96b7cafd27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955464"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="e2665-102">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2665-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="e2665-103">Ek hata ayıklama sembol bilgilerini almak için [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="e2665-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2665-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e2665-104">Methods</span></span>  
  
|<span data-ttu-id="e2665-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e2665-105">Method</span></span>|<span data-ttu-id="e2665-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2665-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2665-107">GetFrameProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2665-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="e2665-108">Bir yöntemin göreli sanal adresini Başlatan yöntemi ve ana çerçeveye kod göreli sanal adres verildiğinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2665-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="e2665-109">GetGenericDictionaryInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2665-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="e2665-110">Genel sözlük eşlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="e2665-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2665-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2665-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2665-112">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2665-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e2665-113">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e2665-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2665-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2665-114">Requirements</span></span>  
 <span data-ttu-id="e2665-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2665-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2665-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2665-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2665-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2665-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2665-118">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2665-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2665-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2665-119">See also</span></span>

- [<span data-ttu-id="e2665-120">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2665-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e2665-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e2665-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e2665-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e2665-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
