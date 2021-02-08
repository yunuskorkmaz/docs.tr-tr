---
description: 'Daha fazla bilgi edinin: WriteableMetadataUpdateMode numaralandırması'
title: WriteableMetadataUpdateMode Numaralandırması
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: b8136963e315c429643bd0ebf4bdb509d5173bec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800519"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="d1c16-103">WriteableMetadataUpdateMode Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d1c16-103">WriteableMetadataUpdateMode Enumeration</span></span>

<span data-ttu-id="d1c16-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="d1c16-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d1c16-105">Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1c16-105">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c16-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1c16-106">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="d1c16-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d1c16-107">Members</span></span>  
  
|<span data-ttu-id="d1c16-108">Üye adı</span><span class="sxs-lookup"><span data-stu-id="d1c16-108">Member name</span></span>|<span data-ttu-id="d1c16-109">Description</span><span class="sxs-lookup"><span data-stu-id="d1c16-109">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="d1c16-110">Meta verilerde bellek içi güncelleştirmeler üzerinde değişiklik yaparken .NET Framework önceki sürümleriyle uyumluluğu koruyun.</span><span class="sxs-lookup"><span data-stu-id="d1c16-110">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="d1c16-111">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d1c16-111">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="d1c16-112">Hata ayıklayıcıda görünür metaveri için bellek içi güncelleştirmeleri yapın.</span><span class="sxs-lookup"><span data-stu-id="d1c16-112">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1c16-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1c16-113">Remarks</span></span>  

 <span data-ttu-id="d1c16-114">Numaralandırma üyesi, `WriteableMetadataUpdateMode` hedef işlemdeki meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıda görünür olup olmadığını denetlemek Için [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d1c16-114">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="d1c16-115">`LegacyCompatPolicy`Seçeneği, 4.5.2 öncesinde .NET Framework sürümleriyle aynı davranışı zorlar.</span><span class="sxs-lookup"><span data-stu-id="d1c16-115">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="d1c16-116">Bu genellikle güncelleştirmelerden meta verilerin görünür olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d1c16-116">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="d1c16-117">Ancak, bir dizi hata ayıklama yöntemine yapılan çağrılar, güncelleştirmeleri görünür hale getirmek için hata ayıklayıcıyı örtülü olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="d1c16-117">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="d1c16-118">Örneğin, hata ayıklayıcı [ICorDebugILFrame:: GetLocalVariable](icordebugilframe-getlocalvariable-method.md) öğesini geçirirse, yöntemin özgün meta verilerinde bulunmayan bir değişkenin dizinini, modülün tüm meta verileri işlemin geçerli durumuyla eşleşen bir anlık görüntüye güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d1c16-118">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="d1c16-119">Diğer bir deyişle, `LegacyCompatPolicy` seçeneğiyle hata ayıklayıcı, yönetilmeyen hata ayıklama API 'sinin diğer bölümlerini nasıl kullandığına bağlı olarak, kullanılabilir meta veri güncelleştirmelerinden hiçbiri, bazılarını veya tümünü görebilir.</span><span class="sxs-lookup"><span data-stu-id="d1c16-119">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c16-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1c16-120">Requirements</span></span>  

 <span data-ttu-id="d1c16-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1c16-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1c16-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1c16-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1c16-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d1c16-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1c16-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1c16-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c16-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1c16-125">See also</span></span>

- [<span data-ttu-id="d1c16-126">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d1c16-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="d1c16-127">SetWriteableMetadataUpdateMode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1c16-127">SetWriteableMetadataUpdateMode Method</span></span>](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
