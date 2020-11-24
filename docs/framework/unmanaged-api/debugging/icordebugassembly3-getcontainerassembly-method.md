---
title: ICorDebugAssembly3::GetContainerAssembly Yöntemi
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 51e68e73983425cdd7d648b6856809fcba590f70
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688555"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="e48dd-102">ICorDebugAssembly3::GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e48dd-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>

<span data-ttu-id="e48dd-103">Bu nesnenin kapsayıcı derlemesini döndürür `ICorDebugAssembly3` .</span><span class="sxs-lookup"><span data-stu-id="e48dd-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e48dd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e48dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e48dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e48dd-105">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="e48dd-106">Kapsayıcı derlemesini temsil eden bir ICorDebugAssembly nesnesinin adresine yönelik bir işaretçi veya yöntem çağrısı başarısız olursa **null** .</span><span class="sxs-lookup"><span data-stu-id="e48dd-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e48dd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e48dd-107">Return Value</span></span>  

 <span data-ttu-id="e48dd-108">`S_OK` Yöntem çağrısı başarılı olursa; Aksi halde, `S_FALSE` , `ppAssembly` ve **null**.</span><span class="sxs-lookup"><span data-stu-id="e48dd-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e48dd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e48dd-109">Remarks</span></span>  

 <span data-ttu-id="e48dd-110">Bu derleme, tek bir kapsayıcı derlemesi içindeki diğer kullanıcılarla birleştirilmişse, bu yöntem kapsayıcı derlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e48dd-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="e48dd-111">Daha fazla bilgi ve terminoloji için [ICorDebugProcess6:: Enablevirtualmodulebölünmesi](icordebugprocess6-enablevirtualmodulesplitting-method.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="e48dd-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e48dd-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e48dd-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e48dd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e48dd-113">Requirements</span></span>  

 <span data-ttu-id="e48dd-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e48dd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e48dd-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e48dd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e48dd-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e48dd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e48dd-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e48dd-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48dd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e48dd-118">See also</span></span>

- [<span data-ttu-id="e48dd-119">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e48dd-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="e48dd-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e48dd-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
