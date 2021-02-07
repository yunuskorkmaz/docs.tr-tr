---
description: 'Daha fazla bilgi edinin: ICorDebugAssembly3:: EnumerateContainedAssemblies yöntemi'
title: ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 8933500713661ef785eb3ce5abc574e512580b6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754088"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="9acc5-103">ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9acc5-103">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>

<span data-ttu-id="9acc5-104">Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="9acc5-104">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9acc5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9acc5-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9acc5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9acc5-106">Parameters</span></span>  

 `ppAssemblies`  
 <span data-ttu-id="9acc5-107">dışı Numaralandırıcı olan ICorDebugAssemblyEnum arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9acc5-107">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9acc5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9acc5-108">Return Value</span></span>  

 <span data-ttu-id="9acc5-109">`S_OK` Bu `ICorDebugAssembly3` nesne bir kapsayıcıdır; Aksi takdirde, `S_FALSE` ve numaralandırması boştur.</span><span class="sxs-lookup"><span data-stu-id="9acc5-109">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9acc5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9acc5-110">Remarks</span></span>  

 <span data-ttu-id="9acc5-111">İçerilen derlemeleri listelemek için semboller gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9acc5-111">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="9acc5-112">Yoksa, yöntemi döndürür `S_FALSE` ve geçerli numaralandırıcı sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="9acc5-112">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9acc5-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9acc5-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9acc5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9acc5-114">Requirements</span></span>  

 <span data-ttu-id="9acc5-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9acc5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9acc5-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9acc5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9acc5-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9acc5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9acc5-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9acc5-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9acc5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9acc5-119">See also</span></span>

- [<span data-ttu-id="9acc5-120">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9acc5-120">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="9acc5-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9acc5-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
