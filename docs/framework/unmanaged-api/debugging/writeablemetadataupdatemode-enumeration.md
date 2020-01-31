---
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
ms.openlocfilehash: 5c3f2f7a9c0804b71c9c8a52bb032aca7c03825e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790299"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="e77f1-102">WriteableMetadataUpdateMode Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e77f1-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="e77f1-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="e77f1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e77f1-104">Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e77f1-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e77f1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e77f1-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="e77f1-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e77f1-106">Members</span></span>  
  
|<span data-ttu-id="e77f1-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="e77f1-107">Member name</span></span>|<span data-ttu-id="e77f1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e77f1-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="e77f1-109">Meta verilerde bellek içi güncelleştirmeler üzerinde değişiklik yaparken .NET Framework önceki sürümleriyle uyumluluğu koruyun.</span><span class="sxs-lookup"><span data-stu-id="e77f1-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="e77f1-110">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e77f1-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="e77f1-111">Hata ayıklayıcıda görünür metaveri için bellek içi güncelleştirmeleri yapın.</span><span class="sxs-lookup"><span data-stu-id="e77f1-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e77f1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e77f1-112">Remarks</span></span>  
 <span data-ttu-id="e77f1-113">Hedef işlemdeki meta verilere yönelik bellek güncelleştirmelerinin hata ayıklayıcıya görünür olup olmadığını denetlemek için `WriteableMetadataUpdateMode` numaralandırmanın bir üyesi [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e77f1-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="e77f1-114">`LegacyCompatPolicy` seçeneği, 4.5.2 önce .NET Framework sürümleriyle aynı davranışı zorlar.</span><span class="sxs-lookup"><span data-stu-id="e77f1-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="e77f1-115">Bu genellikle güncelleştirmelerden meta verilerin görünür olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e77f1-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="e77f1-116">Ancak, bir dizi hata ayıklama yöntemine yapılan çağrılar, güncelleştirmeleri görünür hale getirmek için hata ayıklayıcıyı örtülü olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="e77f1-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="e77f1-117">Örneğin, hata ayıklayıcı [ICorDebugILFrame:: GetLocalVariable](icordebugilframe-getlocalvariable-method.md) öğesini geçirirse, yöntemin özgün meta verilerinde bulunmayan bir değişkenin dizinini, modülün tüm meta verileri işlemin geçerli durumuyla eşleşen bir anlık görüntüye güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e77f1-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="e77f1-118">Diğer bir deyişle, `LegacyCompatPolicy` seçeneği ile, hata ayıklayıcı yönetilmeyen hata ayıklama API 'sinin diğer bölümlerini nasıl kullandığına bağlı olarak, kullanılabilir meta veri güncelleştirmelerinden hiçbiri, bazılarını veya tümünü görebilir.</span><span class="sxs-lookup"><span data-stu-id="e77f1-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e77f1-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e77f1-119">Requirements</span></span>  
 <span data-ttu-id="e77f1-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e77f1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e77f1-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e77f1-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e77f1-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e77f1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e77f1-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e77f1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77f1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e77f1-124">See also</span></span>

- [<span data-ttu-id="e77f1-125">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="e77f1-125">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="e77f1-126">SetWriteableMetadataUpdateMode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e77f1-126">SetWriteableMetadataUpdateMode Method</span></span>](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
