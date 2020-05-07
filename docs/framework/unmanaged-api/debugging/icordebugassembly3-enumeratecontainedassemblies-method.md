---
title: ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: aebf499d7d25caef80782cc5661a57048dc5f6a9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894858"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="590e7-102">ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="590e7-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="590e7-103">Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="590e7-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="590e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="590e7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="590e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="590e7-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="590e7-106">dışı Numaralandırıcı olan ICorDebugAssemblyEnum arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="590e7-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="590e7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="590e7-107">Return Value</span></span>  
 <span data-ttu-id="590e7-108">`S_OK`Bu `ICorDebugAssembly3` nesne bir kapsayıcıdır; Aksi halde `S_FALSE`, ve numaralandırması boştur.</span><span class="sxs-lookup"><span data-stu-id="590e7-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="590e7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="590e7-109">Remarks</span></span>  
 <span data-ttu-id="590e7-110">İçerilen derlemeleri listelemek için semboller gereklidir.</span><span class="sxs-lookup"><span data-stu-id="590e7-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="590e7-111">Yoksa, yöntemi döndürür `S_FALSE`ve geçerli numaralandırıcı sağlanmaz.</span><span class="sxs-lookup"><span data-stu-id="590e7-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="590e7-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="590e7-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="590e7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="590e7-113">Requirements</span></span>  
 <span data-ttu-id="590e7-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="590e7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="590e7-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="590e7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="590e7-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="590e7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="590e7-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="590e7-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590e7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="590e7-118">See also</span></span>

- [<span data-ttu-id="590e7-119">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="590e7-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="590e7-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="590e7-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
