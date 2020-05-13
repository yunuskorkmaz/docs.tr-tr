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
ms.openlocfilehash: 6de75e1e27660ac91bd6320a501db47f3b055fb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212262"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="4b6d4-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b6d4-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="4b6d4-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="4b6d4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4b6d4-104">Hata ayıklayıcının, hedef işlem içindeki meta veriler için bellek içi güncelleştirmeleri nasıl işlediğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b6d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b6d4-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b6d4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b6d4-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="4b6d4-107">Hedef işlemdeki meta verilere yönelik bellek güncelleştirmelerinin görünür olup olmadığını belirten bir [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) numaralandırma değeri ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) ve `WriteableMetadataUpdateMode::LegacyCompatPolicy` hata ayıklayıcıya görünür değil.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-107">A [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b6d4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b6d4-108">Remarks</span></span>  
 <span data-ttu-id="4b6d4-109">Hedef işlemin meta verilerinde yapılan güncelleştirmeler, düzenleme ve devam etme, profil oluşturucu veya ile gelebilir <xref:System.Reflection.Emit?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4b6d4-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b6d4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b6d4-110">Requirements</span></span>  
 <span data-ttu-id="4b6d4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b6d4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b6d4-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4b6d4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b6d4-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4b6d4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b6d4-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b6d4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b6d4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b6d4-115">See also</span></span>

- [<span data-ttu-id="4b6d4-116">ICorDebugProcess7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b6d4-116">ICorDebugProcess7 Interface</span></span>](icordebugprocess7-interface.md)
- [<span data-ttu-id="4b6d4-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4b6d4-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
