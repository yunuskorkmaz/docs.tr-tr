---
description: ': ICorDebugManagedCallback:: LoadClass Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugManagedCallback::LoadClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 6f670a2f0798c7edfdc4292334cf9534e59a3007
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660615"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="1d728-103">ICorDebugManagedCallback::LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d728-103">ICorDebugManagedCallback::LoadClass Method</span></span>

<span data-ttu-id="1d728-104">Bir sınıfın yüklendiğini hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="1d728-104">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d728-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d728-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d728-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d728-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="1d728-107">'ndaki Sınıfın yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1d728-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="1d728-108">'ndaki Sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1d728-108">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d728-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d728-109">Remarks</span></span>  

 <span data-ttu-id="1d728-110">Bu geri çağırma, yalnızca sınıf yüklemesi sınıfı içeren modül için etkinleştirildiyse oluşur.</span><span class="sxs-lookup"><span data-stu-id="1d728-110">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="1d728-111">Sınıf yükleme her zaman dinamik modüller için etkindir.</span><span class="sxs-lookup"><span data-stu-id="1d728-111">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="1d728-112">`LoadClass`Geri arama, kesme noktalarını dinamik modüllerde yeni oluşturulan sınıflara bağlamak için uygun bir zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d728-112">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d728-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d728-113">Requirements</span></span>  

 <span data-ttu-id="1d728-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d728-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d728-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1d728-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d728-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1d728-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d728-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d728-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d728-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d728-118">See also</span></span>

- [<span data-ttu-id="1d728-119">UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d728-119">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="1d728-120">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d728-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
