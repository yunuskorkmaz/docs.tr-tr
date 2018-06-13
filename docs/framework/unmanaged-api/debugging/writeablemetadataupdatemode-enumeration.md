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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fbf9a24c350dd4c33bb50b0add8817c8922925f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436013"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="3b3d1-102">WriteableMetadataUpdateMode Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3b3d1-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="3b3d1-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="3b3d1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3b3d1-104">Bellek içi güncelleştirmeleri meta verilerinin bir hata ayıklayıcısı görünür olup olmadığını belirten değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b3d1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b3d1-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="3b3d1-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3b3d1-106">Members</span></span>  
  
|<span data-ttu-id="3b3d1-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="3b3d1-107">Member name</span></span>|<span data-ttu-id="3b3d1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b3d1-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="3b3d1-109">Bellek içi güncelleştirmeleri meta verileri görünür yaparken, .NET Framework'ün önceki sürümleriyle uyumluluğunu korumak.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="3b3d1-110">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="3b3d1-111">Bellek içi güncelleştirmeleri meta verileri için hata ayıklayıcı görünür kılma.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b3d1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b3d1-112">Remarks</span></span>  
 <span data-ttu-id="3b3d1-113">Üye `WriteableMetadataUpdateMode` numaralandırması için geçirilebilir [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) bellek içi hedef işleminde meta veri güncelleştirmeleri olup olmadığını denetlemek için yöntemi için hata ayıklayıcı görünür.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="3b3d1-114">`LegacyCompatPolicy` Seçeneği .NET Framework 4.5.2 önce sürümlerindekilerle aynı davranışı zorlar.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="3b3d1-115">Genellikle bu meta veri güncelleştirmelerin yani görünür değil.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="3b3d1-116">Ancak, bir dizi hata ayıklama yöntem çağrıları, güncelleştirmelerinin görünür olması için hata ayıklayıcı örtük olarak coerce.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="3b3d1-117">Örneğin, hata ayıklayıcı geçerse [Icordebugılframe::getlocalvariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) dizini bir değişkenin modülü geçerli durumunu eşleşen bir anlık görüntüye güncelleştirilmiş yöntemin özgün meta verilerde, tüm meta veri bulunamadı işlem.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="3b3d1-118">Diğer bir deyişle, ile `LegacyCompatPolicy` seçeneği, hata ayıklayıcı yok, bazı veya tüm diğer bölümleri yönetilmeyen hata ayıklama API'si kullanma bağlı olarak kullanılabilir meta veri güncelleştirmeleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b3d1-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b3d1-119">Requirements</span></span>  
 <span data-ttu-id="3b3d1-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b3d1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b3d1-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b3d1-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b3d1-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b3d1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b3d1-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b3d1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b3d1-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b3d1-124">See Also</span></span>  
 [<span data-ttu-id="3b3d1-125">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="3b3d1-125">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="3b3d1-126">SetWriteableMetadataUpdateMode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b3d1-126">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
