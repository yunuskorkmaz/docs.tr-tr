---
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
ms.openlocfilehash: cc5a2e1de79d6ba04ff3bf2bf86e0cb7ce9a5c0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788383"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="68341-102">ICorDebugManagedCallback::LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68341-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="68341-103">Bir sınıfın yüklendiğini hata ayıklayıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="68341-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68341-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68341-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68341-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68341-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="68341-106">'ndaki Sınıfın yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="68341-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="68341-107">'ndaki Sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="68341-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68341-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68341-108">Remarks</span></span>  
 <span data-ttu-id="68341-109">Bu geri çağırma, yalnızca sınıf yüklemesi sınıfı içeren modül için etkinleştirildiyse oluşur.</span><span class="sxs-lookup"><span data-stu-id="68341-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="68341-110">Sınıf yükleme her zaman dinamik modüller için etkindir.</span><span class="sxs-lookup"><span data-stu-id="68341-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="68341-111">`LoadClass` geri çağırması, kesme noktalarını dinamik modüllerde yeni oluşturulan sınıflara bağlamak için uygun bir zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="68341-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68341-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68341-112">Requirements</span></span>  
 <span data-ttu-id="68341-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68341-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68341-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="68341-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68341-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="68341-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68341-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68341-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68341-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68341-117">See also</span></span>

- [<span data-ttu-id="68341-118">UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68341-118">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="68341-119">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68341-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
