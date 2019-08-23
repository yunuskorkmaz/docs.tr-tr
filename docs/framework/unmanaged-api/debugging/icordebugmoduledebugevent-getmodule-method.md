---
title: 'Icordebugmoduledebuggevent:: GetModule yöntemi'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e68fab11a881854ae4c3fe073f73150694d31ae5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965103"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="af000-102">Icordebugmoduledebuggevent:: GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="af000-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="af000-103">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="af000-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af000-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af000-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af000-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af000-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="af000-106">dışı Yeni yüklenen veya kaldırılan birleştirilmiş modülü temsil eden ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="af000-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af000-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af000-107">Remarks</span></span>  
 <span data-ttu-id="af000-108">Modülün yüklenip yüklenmediğini veya bellekten kaldırılmadığını anlamak için [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metodunu çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af000-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af000-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af000-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af000-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af000-110">Requirements</span></span>  
 <span data-ttu-id="af000-111">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af000-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af000-112">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="af000-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af000-113">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="af000-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af000-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af000-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af000-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af000-115">See also</span></span>

- [<span data-ttu-id="af000-116">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af000-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="af000-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="af000-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
