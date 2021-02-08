---
description: 'Daha fazla bilgi edinin: ılcodekind numaralandırması'
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
ms.openlocfilehash: 2d3163b2c601c6f53d9a532fa877c014a67b3e18
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790470"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="f187e-103">ILCodeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f187e-103">ILCodeKind Enumeration</span></span>

<span data-ttu-id="f187e-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="f187e-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f187e-105">Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f187e-105">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f187e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f187e-106">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="f187e-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f187e-107">Members</span></span>  
  
|<span data-ttu-id="f187e-108">Üye adı</span><span class="sxs-lookup"><span data-stu-id="f187e-108">Member name</span></span>|<span data-ttu-id="f187e-109">Description</span><span class="sxs-lookup"><span data-stu-id="f187e-109">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="f187e-110">Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="f187e-110">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="f187e-111">Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="f187e-111">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f187e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f187e-112">Remarks</span></span>  

 <span data-ttu-id="f187e-113">`ILCodeKind`Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere [](icordebugilframe4-enumeratelocalvariablesex-method.md) erişip erişemeyeceğini ve hata ayıklayıcının [](icordebugilframe4-getlocalvariableex-method.md) belgelenmiş Il 'ye erişip erişemeyeceğini anlamak için [GetCodeEx](icordebugilframe4-getcodeex-method.md) yöntemine bir numaralandırma üyesi iletilebilir.</span><span class="sxs-lookup"><span data-stu-id="f187e-113">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f187e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f187e-114">Requirements</span></span>  

 <span data-ttu-id="f187e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f187e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f187e-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f187e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f187e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f187e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f187e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f187e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f187e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f187e-119">See also</span></span>

- [<span data-ttu-id="f187e-120">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f187e-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="f187e-121">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f187e-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="f187e-122">ReJIT: A How-To Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f187e-122">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
