---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: d8c91c10577efd6a76af778cd01002de006df43a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209883"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="8c9a9-102">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="8c9a9-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="8c9a9-103">Yüklenen modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="8c9a9-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c9a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c9a9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c9a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c9a9-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="8c9a9-106">dışı Yüklenen modülün temel adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8c9a9-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c9a9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c9a9-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c9a9-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8c9a9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c9a9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c9a9-109">Requirements</span></span>  
 <span data-ttu-id="8c9a9-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c9a9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c9a9-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8c9a9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c9a9-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8c9a9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c9a9-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c9a9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c9a9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c9a9-114">See also</span></span>

- [<span data-ttu-id="8c9a9-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c9a9-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="8c9a9-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c9a9-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
