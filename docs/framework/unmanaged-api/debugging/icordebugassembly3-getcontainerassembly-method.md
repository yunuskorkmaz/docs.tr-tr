---
title: ICorDebugAssembly3::GetContainerAssembly Yöntemi
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 969cca6d5613670fc4b26fc973785b4874c3684c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778067"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="09067-102">ICorDebugAssembly3::GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09067-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="09067-103">Bu `ICorDebugAssembly3` nesnesinin kapsayıcı derlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="09067-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09067-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09067-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09067-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09067-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="09067-106">Kapsayıcı derlemesini temsil eden bir ICorDebugAssembly nesnesinin adresine yönelik bir işaretçi veya yöntem çağrısı başarısız olursa **null** .</span><span class="sxs-lookup"><span data-stu-id="09067-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09067-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="09067-107">Return Value</span></span>  
 <span data-ttu-id="09067-108">Yöntem çağrısı başarılı olursa `S_OK`; Aksi takdirde, `S_FALSE`ve `ppAssembly` **null**.</span><span class="sxs-lookup"><span data-stu-id="09067-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09067-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09067-109">Remarks</span></span>  
 <span data-ttu-id="09067-110">Bu derleme, tek bir kapsayıcı derlemesi içindeki diğer kullanıcılarla birleştirilmişse, bu yöntem kapsayıcı derlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="09067-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="09067-111">Daha fazla bilgi ve terminoloji için [ICorDebugProcess6:: Enablevirtualmodulebölünmesi](icordebugprocess6-enablevirtualmodulesplitting-method.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="09067-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09067-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="09067-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09067-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09067-113">Requirements</span></span>  
 <span data-ttu-id="09067-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09067-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09067-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="09067-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09067-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="09067-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09067-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09067-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09067-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09067-118">See also</span></span>

- [<span data-ttu-id="09067-119">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09067-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="09067-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="09067-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
