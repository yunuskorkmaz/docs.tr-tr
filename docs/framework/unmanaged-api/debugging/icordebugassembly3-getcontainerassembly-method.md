---
title: ICorDebugAssembly3::GetContainerAssembly Yöntemi
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9bd4cd44eca9b12ab8773fd75b6262579cfe8e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645520"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="89e0c-102">ICorDebugAssembly3::GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89e0c-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="89e0c-103">Bu kapsayıcı derleme döndürür `ICorDebugAssembly3` nesne.</span><span class="sxs-lookup"><span data-stu-id="89e0c-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89e0c-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89e0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89e0c-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="89e0c-106">Kapsayıcı derlemesi temsil eden Icordebugassembly nesnenin adresini bir işaretçiye veya **null** yöntem çağrısı başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="89e0c-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89e0c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89e0c-107">Return Value</span></span>  
 <span data-ttu-id="89e0c-108">`S_OK` metot çağrısı başarılı olursa; Aksi takdirde, `S_FALSE`, ve `ppAssembly` olduğu **null**.</span><span class="sxs-lookup"><span data-stu-id="89e0c-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89e0c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89e0c-109">Remarks</span></span>  
 <span data-ttu-id="89e0c-110">Bu derleme başkalarıyla tek kapsayıcı derleme içinde birleştirilmiştir, bu yöntem, kapsayıcı derleme döndürür.</span><span class="sxs-lookup"><span data-stu-id="89e0c-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="89e0c-111">Daha fazla bilgi ve terimler için bkz. [Icordebugprocess6::enablevirtualmodulesplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) konu.</span><span class="sxs-lookup"><span data-stu-id="89e0c-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89e0c-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89e0c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89e0c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89e0c-113">Requirements</span></span>  
 <span data-ttu-id="89e0c-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89e0c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89e0c-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89e0c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89e0c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89e0c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89e0c-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89e0c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e0c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89e0c-118">See also</span></span>

- [<span data-ttu-id="89e0c-119">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89e0c-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="89e0c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="89e0c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
