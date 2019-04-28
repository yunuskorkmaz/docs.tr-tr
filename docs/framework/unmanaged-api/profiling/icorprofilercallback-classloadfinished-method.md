---
title: ICorProfilerCallback::ClassLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cab4b039d225f4ee1b00add6ffec63fd35be8857
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597997"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="ae7e2-102">ICorProfilerCallback::ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae7e2-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="ae7e2-103">Profil Oluşturucu, bir sınıf yükleme işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="ae7e2-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae7e2-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae7e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae7e2-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="ae7e2-106">[in] Yüklenen sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae7e2-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ae7e2-107">[in] Sınıf başarıyla yüklü olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ae7e2-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae7e2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae7e2-108">Remarks</span></span>  
 <span data-ttu-id="ae7e2-109">Değerini `classId` kadar bir bilgi isteği için geçerli değil `ClassLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ae7e2-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="ae7e2-110">Sınıf yükleme bazı bölümleri sonra devam edebilir `ClassLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ae7e2-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="ae7e2-111">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae7e2-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ae7e2-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü sınıfı yükleme işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae7e2-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae7e2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae7e2-113">Requirements</span></span>  
 <span data-ttu-id="ae7e2-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae7e2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae7e2-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae7e2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae7e2-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae7e2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae7e2-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae7e2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7e2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae7e2-118">See also</span></span>

- [<span data-ttu-id="ae7e2-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae7e2-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ae7e2-120">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae7e2-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
