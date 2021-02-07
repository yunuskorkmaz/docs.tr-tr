---
description: 'Daha fazla bilgi edinin: ICorDebugDataTarget3 Interface'
title: ICorDebugDataTarget3 Arabirimi
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: fa786b920d1a2e72dc2a7918e0514773862a0e85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710445"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="9f69b-103">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f69b-103">ICorDebugDataTarget3 Interface</span></span>

<span data-ttu-id="9f69b-104">Yüklü modüller hakkında bilgi sağlamak için [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="9f69b-104">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="9f69b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9f69b-105">Method</span></span>  
  
|<span data-ttu-id="9f69b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9f69b-106">Method</span></span>|<span data-ttu-id="9f69b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f69b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f69b-108">GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f69b-108">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="9f69b-109">Şimdiye kadar yüklenmiş modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="9f69b-109">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f69b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f69b-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f69b-111">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f69b-111">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9f69b-112">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="9f69b-112">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f69b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f69b-113">Requirements</span></span>  

 <span data-ttu-id="9f69b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f69b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f69b-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9f69b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f69b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9f69b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f69b-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f69b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f69b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f69b-118">See also</span></span>

- [<span data-ttu-id="9f69b-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9f69b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9f69b-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9f69b-120">Debugging</span></span>](index.md)
