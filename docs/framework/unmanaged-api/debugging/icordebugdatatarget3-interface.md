---
title: ICorDebugDataTarget3 Arabirimi
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 57ef9b567d57c77c523ca6daefcf80b1d7de66d1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976414"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="762ac-102">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="762ac-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="762ac-103">Yüklü modüller hakkında bilgi sağlamak için [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="762ac-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="762ac-104">Yöntem</span><span class="sxs-lookup"><span data-stu-id="762ac-104">Method</span></span>  
  
|<span data-ttu-id="762ac-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="762ac-105">Method</span></span>|<span data-ttu-id="762ac-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="762ac-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="762ac-107">GetLoadedModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="762ac-107">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="762ac-108">Şimdiye kadar yüklenmiş modüllerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="762ac-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="762ac-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="762ac-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="762ac-110">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="762ac-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="762ac-111">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="762ac-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="762ac-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="762ac-112">Requirements</span></span>  
 <span data-ttu-id="762ac-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="762ac-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="762ac-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="762ac-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="762ac-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="762ac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="762ac-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="762ac-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="762ac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="762ac-117">See also</span></span>

- [<span data-ttu-id="762ac-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="762ac-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="762ac-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="762ac-119">Debugging</span></span>](index.md)
