---
description: ': ICorDebugLoadedModule:: GetBaseAddress yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 2852131d543cfb9593cf4ff607d1f752226c2880
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801273"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="f3fed-103">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="f3fed-103">ICorDebugLoadedModule::GetBaseAddress Method</span></span>

<span data-ttu-id="f3fed-104">Yüklenen modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="f3fed-104">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fed-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3fed-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3fed-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3fed-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="f3fed-107">dışı Yüklenen modülün temel adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3fed-107">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3fed-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3fed-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3fed-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3fed-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3fed-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3fed-110">Requirements</span></span>  

 <span data-ttu-id="f3fed-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3fed-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3fed-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3fed-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3fed-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f3fed-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3fed-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3fed-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fed-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3fed-115">See also</span></span>

- [<span data-ttu-id="f3fed-116">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3fed-116">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f3fed-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f3fed-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
