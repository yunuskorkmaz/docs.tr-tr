---
title: ILCodeKind Numaralandırması
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: b9d27c3e3cd42039aeefcb517ecc81eadeb5c183
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557430"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="6703a-102">ILCodeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6703a-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="6703a-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="6703a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6703a-104">Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6703a-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6703a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6703a-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="6703a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6703a-106">Members</span></span>  
  
|<span data-ttu-id="6703a-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="6703a-107">Member name</span></span>|<span data-ttu-id="6703a-108">Description</span><span class="sxs-lookup"><span data-stu-id="6703a-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="6703a-109">Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="6703a-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="6703a-110">Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="6703a-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6703a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6703a-111">Remarks</span></span>  
 <span data-ttu-id="6703a-112">`ILCodeKind`Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) erişip erişemeyeceğini ve hata ayıklayıcının [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) belgelenmiş Il 'ye erişip erişemeyeceğini anlamak için [GetCodeEx](icordebugilframe4-getcodeex-method.md) yöntemine bir numaralandırma üyesi iletilebilir.</span><span class="sxs-lookup"><span data-stu-id="6703a-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6703a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6703a-113">Requirements</span></span>  
 <span data-ttu-id="6703a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6703a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6703a-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6703a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6703a-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6703a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6703a-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6703a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6703a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6703a-118">See also</span></span>

- [<span data-ttu-id="6703a-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="6703a-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="6703a-120">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6703a-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="6703a-121">ReJIT: nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6703a-121">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
