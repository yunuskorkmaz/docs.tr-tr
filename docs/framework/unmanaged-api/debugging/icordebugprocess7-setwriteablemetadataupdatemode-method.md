---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess7:: SetWriteableMetadataUpdateMode yöntemi'
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
ms.openlocfilehash: 86ece68e160fbd61f44adcf495656c7b5d6b5153
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691269"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="3d4cf-103">ICorDebugProcess7::SetWriteableMetadataUpdateMode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d4cf-103">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>

<span data-ttu-id="3d4cf-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="3d4cf-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3d4cf-105">Hata ayıklayıcının, hedef işlem içindeki meta veriler için bellek içi güncelleştirmeleri nasıl işlediğini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="3d4cf-105">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d4cf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d4cf-106">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d4cf-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d4cf-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="3d4cf-108">Hedef işlemdeki meta verilere yönelik bellek güncelleştirmelerinin görünür olup olmadığını belirten bir [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) numaralandırma değeri ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) ve `WriteableMetadataUpdateMode::LegacyCompatPolicy` hata ayıklayıcıya görünür değil.</span><span class="sxs-lookup"><span data-stu-id="3d4cf-108">A [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d4cf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d4cf-109">Remarks</span></span>  

 <span data-ttu-id="3d4cf-110">Hedef işlemin meta verilerinde yapılan güncelleştirmeler, düzenleme ve devam etme, profil oluşturucu veya ile gelebilir <xref:System.Reflection.Emit?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3d4cf-110">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d4cf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d4cf-111">Requirements</span></span>  

 <span data-ttu-id="3d4cf-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d4cf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d4cf-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3d4cf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d4cf-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3d4cf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d4cf-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d4cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4cf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d4cf-116">See also</span></span>

- [<span data-ttu-id="3d4cf-117">ICorDebugProcess7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d4cf-117">ICorDebugProcess7 Interface</span></span>](icordebugprocess7-interface.md)
- [<span data-ttu-id="3d4cf-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3d4cf-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
