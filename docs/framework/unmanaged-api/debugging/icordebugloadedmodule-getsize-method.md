---
description: ': ICorDebugLoadedModule:: GetSize yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugLoadedModule::GetSize Metodu
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 6701d2578559a039f352df19bf9e859658c6687f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801247"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="35cff-103">ICorDebugLoadedModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="35cff-103">ICorDebugLoadedModule::GetSize Method</span></span>

<span data-ttu-id="35cff-104">Yüklenen modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="35cff-104">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35cff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35cff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35cff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35cff-106">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="35cff-107">dışı Yüklenen modüldeki bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35cff-107">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35cff-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35cff-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35cff-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35cff-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35cff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35cff-110">Requirements</span></span>  

 <span data-ttu-id="35cff-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35cff-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35cff-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35cff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35cff-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="35cff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35cff-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35cff-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35cff-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35cff-115">See also</span></span>

- [<span data-ttu-id="35cff-116">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="35cff-116">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="35cff-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="35cff-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
