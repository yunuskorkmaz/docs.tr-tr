---
description: ': Icordebugmoduledebuggevent:: GetModule yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmoduledebuggevent:: GetModule yöntemi'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: c6d7171da231576ff90f54aaefe4b473af0afd40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790743"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="7ac13-103">Icordebugmoduledebuggevent:: GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ac13-103">ICorDebugModuleDebugEvent::GetModule Method</span></span>

<span data-ttu-id="7ac13-104">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="7ac13-104">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ac13-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ac13-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ac13-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ac13-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="7ac13-107">dışı Yeni yüklenen veya kaldırılan birleştirilmiş modülü temsil eden ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7ac13-107">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ac13-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ac13-108">Remarks</span></span>  

 <span data-ttu-id="7ac13-109">Modülün yüklenip yüklenmediğini veya bellekten kaldırılmadığını anlamak için [GetEventKind](icordebugdebugevent-geteventkind-method.md) metodunu çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ac13-109">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ac13-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ac13-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ac13-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ac13-111">Requirements</span></span>  

 <span data-ttu-id="7ac13-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ac13-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ac13-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7ac13-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ac13-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7ac13-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ac13-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ac13-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ac13-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ac13-116">See also</span></span>

- [<span data-ttu-id="7ac13-117">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ac13-117">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="7ac13-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7ac13-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
