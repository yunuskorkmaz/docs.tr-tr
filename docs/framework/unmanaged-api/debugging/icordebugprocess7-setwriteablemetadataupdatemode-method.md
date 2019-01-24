---
title: ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90136bd8a84cedebbfbb4848e763a1eaab293102
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533708"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="30ea3-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30ea3-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="30ea3-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="30ea3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="30ea3-104">Hata ayıklayıcı hedef işlem dahilindeki meta veriler için bellek içi güncelleştirmeleri nasıl işlediğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="30ea3-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ea3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30ea3-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30ea3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30ea3-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="30ea3-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) hedef işlemde meta veriler için bellek içi güncelleştirmeleri görünür olup olmadığını belirten sabit listesi değeri (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) veya görünür (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) hata ayıklayıcı.</span><span class="sxs-lookup"><span data-stu-id="30ea3-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30ea3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30ea3-108">Remarks</span></span>  
 <span data-ttu-id="30ea3-109">Hedef işlemin meta veri güncelleştirmeleri, Düzenle ve devam et, bir profil oluşturucu gelebilir veya <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30ea3-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30ea3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30ea3-110">Requirements</span></span>  
 <span data-ttu-id="30ea3-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30ea3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30ea3-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30ea3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30ea3-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30ea3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30ea3-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30ea3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ea3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30ea3-115">See also</span></span>
- [<span data-ttu-id="30ea3-116">ICorDebugProcess7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30ea3-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)
- [<span data-ttu-id="30ea3-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="30ea3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
