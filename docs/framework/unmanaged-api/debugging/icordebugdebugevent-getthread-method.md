---
description: ': Icordebugdebugger gevent:: GetThread Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugDebugEvent::GetThread Yöntemi
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 1d476603572f31882f481d414e483c6712f1b5fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710419"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="de915-103">ICorDebugDebugEvent::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="de915-103">ICorDebugDebugEvent::GetThread Method</span></span>

<span data-ttu-id="de915-104">Olayın gerçekleştiği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="de915-104">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de915-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de915-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de915-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de915-106">Parameters</span></span>  

 <span data-ttu-id="de915-107">ppThread</span><span class="sxs-lookup"><span data-stu-id="de915-107">ppThread</span></span>  
 <span data-ttu-id="de915-108">dışı Olayın gerçekleştiği iş parçacığını temsil eden ICorDebugThread nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="de915-108">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de915-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de915-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de915-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de915-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de915-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de915-111">Requirements</span></span>  

 <span data-ttu-id="de915-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de915-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de915-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="de915-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de915-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="de915-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de915-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de915-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de915-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de915-116">See also</span></span>

- [<span data-ttu-id="de915-117">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de915-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="de915-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="de915-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
