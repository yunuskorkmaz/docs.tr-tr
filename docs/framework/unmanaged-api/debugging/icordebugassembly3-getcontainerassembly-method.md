---
title: ICorDebugAssembly3::GetContainerAssembly Yöntemi
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 39f8dd042ea785258dfe5c048ebc348852be6892
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095386"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="ae01a-102">ICorDebugAssembly3::GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae01a-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="ae01a-103">Bu `ICorDebugAssembly3` nesnesinin kapsayıcı derlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae01a-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae01a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae01a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae01a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae01a-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="ae01a-106">Kapsayıcı derlemesini temsil eden bir ICorDebugAssembly nesnesinin adresine yönelik bir işaretçi veya yöntem çağrısı başarısız olursa **null** .</span><span class="sxs-lookup"><span data-stu-id="ae01a-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae01a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae01a-107">Return Value</span></span>  
 <span data-ttu-id="ae01a-108">Yöntem çağrısı başarılı olursa `S_OK`; Aksi takdirde, `S_FALSE`ve `ppAssembly` **null**.</span><span class="sxs-lookup"><span data-stu-id="ae01a-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae01a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae01a-109">Remarks</span></span>  
 <span data-ttu-id="ae01a-110">Bu derleme, tek bir kapsayıcı derlemesi içindeki diğer kullanıcılarla birleştirilmişse, bu yöntem kapsayıcı derlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae01a-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="ae01a-111">Daha fazla bilgi ve terminoloji için [ICorDebugProcess6:: Enablevirtualmodulebölünmesi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="ae01a-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae01a-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae01a-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae01a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae01a-113">Requirements</span></span>  
 <span data-ttu-id="ae01a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae01a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae01a-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae01a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae01a-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae01a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae01a-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae01a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae01a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae01a-118">See also</span></span>

- [<span data-ttu-id="ae01a-119">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae01a-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="ae01a-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ae01a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
