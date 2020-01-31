---
title: 'Icordebugmoduledebuggevent:: GetModule yöntemi'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 4d9eea8fb5c42002763a0ae52a186bf2c1e6d2ee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792913"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="31d9a-102">Icordebugmoduledebuggevent:: GetModule yöntemi</span><span class="sxs-lookup"><span data-stu-id="31d9a-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="31d9a-103">Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.</span><span class="sxs-lookup"><span data-stu-id="31d9a-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31d9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31d9a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31d9a-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="31d9a-106">dışı Yeni yüklenen veya kaldırılan birleştirilmiş modülü temsil eden ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="31d9a-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31d9a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31d9a-107">Remarks</span></span>  
 <span data-ttu-id="31d9a-108">Modülün yüklenip yüklenmediğini veya bellekten kaldırılmadığını anlamak için [GetEventKind](icordebugdebugevent-geteventkind-method.md) metodunu çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31d9a-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31d9a-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31d9a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d9a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31d9a-110">Requirements</span></span>  
 <span data-ttu-id="31d9a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31d9a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d9a-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="31d9a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31d9a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="31d9a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31d9a-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d9a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d9a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31d9a-115">See also</span></span>

- [<span data-ttu-id="31d9a-116">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31d9a-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="31d9a-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="31d9a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
