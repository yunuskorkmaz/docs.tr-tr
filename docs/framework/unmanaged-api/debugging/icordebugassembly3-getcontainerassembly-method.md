---
description: ': ICorDebugAssembly3:: GetContainerAssembly yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugAssembly3::GetContainerAssembly Yöntemi
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 5a6bc6dfb1c8403137a9444ff1cc4f64e75da65d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791523"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="4205a-103">ICorDebugAssembly3::GetContainerAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4205a-103">ICorDebugAssembly3::GetContainerAssembly Method</span></span>

<span data-ttu-id="4205a-104">Bu nesnenin kapsayıcı derlemesini döndürür `ICorDebugAssembly3` .</span><span class="sxs-lookup"><span data-stu-id="4205a-104">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4205a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4205a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4205a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4205a-106">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="4205a-107">Kapsayıcı derlemesini temsil eden bir ICorDebugAssembly nesnesinin adresine yönelik bir işaretçi veya yöntem çağrısı başarısız olursa **null** .</span><span class="sxs-lookup"><span data-stu-id="4205a-107">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4205a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4205a-108">Return Value</span></span>  

 <span data-ttu-id="4205a-109">`S_OK` Yöntem çağrısı başarılı olursa; Aksi halde, `S_FALSE` , `ppAssembly` ve **null**.</span><span class="sxs-lookup"><span data-stu-id="4205a-109">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4205a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4205a-110">Remarks</span></span>  

 <span data-ttu-id="4205a-111">Bu derleme, tek bir kapsayıcı derlemesi içindeki diğer kullanıcılarla birleştirilmişse, bu yöntem kapsayıcı derlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4205a-111">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="4205a-112">Daha fazla bilgi ve terminoloji için [ICorDebugProcess6:: Enablevirtualmodulebölünmesi](icordebugprocess6-enablevirtualmodulesplitting-method.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="4205a-112">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4205a-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4205a-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4205a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4205a-114">Requirements</span></span>  

 <span data-ttu-id="4205a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4205a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4205a-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4205a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4205a-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4205a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4205a-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4205a-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4205a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4205a-119">See also</span></span>

- [<span data-ttu-id="4205a-120">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4205a-120">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="4205a-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4205a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
