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
ms.openlocfilehash: 0586b9e184a0958b978837601db002e035881cbc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421039"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="acbae-102">ILCodeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="acbae-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="acbae-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="acbae-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="acbae-104">Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="acbae-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acbae-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="acbae-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="acbae-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="acbae-106">Members</span></span>  
  
|<span data-ttu-id="acbae-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="acbae-107">Member name</span></span>|<span data-ttu-id="acbae-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acbae-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="acbae-109">Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi yok.</span><span class="sxs-lookup"><span data-stu-id="acbae-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="acbae-110">Hata ayıklayıcının, ReJIT araçlarından bilgilere erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="acbae-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acbae-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acbae-111">Remarks</span></span>  
 <span data-ttu-id="acbae-112">`ILCodeKind`Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) erişip erişemeyeceğini ve hata ayıklayıcının [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) belgelenmiş Il 'ye erişip erişemeyeceğini anlamak için [GetCodeEx](icordebugilframe4-getcodeex-method.md) yöntemine bir numaralandırma üyesi iletilebilir.</span><span class="sxs-lookup"><span data-stu-id="acbae-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acbae-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acbae-113">Requirements</span></span>  
 <span data-ttu-id="acbae-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acbae-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acbae-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="acbae-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acbae-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="acbae-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acbae-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acbae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acbae-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acbae-118">See also</span></span>

- [<span data-ttu-id="acbae-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="acbae-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="acbae-120">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="acbae-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="acbae-121">ReJIT: nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="acbae-121">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
