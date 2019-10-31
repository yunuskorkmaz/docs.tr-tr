---
title: ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 032f32a08efa92cea682b0e2fc974dc607a9dca4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133947"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="89f48-102">ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89f48-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="89f48-103">Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="89f48-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89f48-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89f48-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89f48-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89f48-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="89f48-106">dışı Numaralandırıcı olan ICorDebugAssemblyEnum arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="89f48-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89f48-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89f48-107">Return Value</span></span>  
 <span data-ttu-id="89f48-108">Bu `ICorDebugAssembly3` nesne bir kapsayıcı ise `S_OK`; Aksi takdirde, `S_FALSE`ve numaralandırma boştur.</span><span class="sxs-lookup"><span data-stu-id="89f48-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89f48-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89f48-109">Remarks</span></span>  
 <span data-ttu-id="89f48-110">İçerilen derlemeleri listelemek için semboller gereklidir.</span><span class="sxs-lookup"><span data-stu-id="89f48-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="89f48-111">Yoksa, yöntem `S_FALSE`döndürür ve geçerli numaralandırıcı sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="89f48-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89f48-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89f48-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89f48-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89f48-113">Requirements</span></span>  
 <span data-ttu-id="89f48-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89f48-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89f48-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="89f48-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89f48-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="89f48-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89f48-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89f48-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f48-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89f48-118">See also</span></span>

- [<span data-ttu-id="89f48-119">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89f48-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="89f48-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="89f48-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
