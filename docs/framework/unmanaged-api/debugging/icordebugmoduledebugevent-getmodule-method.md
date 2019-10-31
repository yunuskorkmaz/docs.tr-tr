---
title: 'Icordebugmoduledebuggevent:: GetModule yöntemi'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 5dc26d0367d01bc8da957c3ce648c3e529dddb08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096932"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="f03f6-102">Icordebugmoduledebuggevent:: GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="f03f6-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="f03f6-103">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="f03f6-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f03f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f03f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f03f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f03f6-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="f03f6-106">dışı Yeni yüklenen veya kaldırılan birleştirilmiş modülü temsil eden ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f03f6-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f03f6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f03f6-107">Remarks</span></span>  
 <span data-ttu-id="f03f6-108">Modülün yüklenip yüklenmediğini veya bellekten kaldırılmadığını anlamak için [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metodunu çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03f6-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f03f6-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f03f6-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f03f6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f03f6-110">Requirements</span></span>  
 <span data-ttu-id="f03f6-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f03f6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f03f6-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f03f6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f03f6-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f03f6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f03f6-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f03f6-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f03f6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f03f6-115">See also</span></span>

- [<span data-ttu-id="f03f6-116">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f03f6-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="f03f6-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f03f6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
