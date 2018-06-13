---
title: CorpubPublish Ortak Sınıfı
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9941a9be7d9f68255636b405db29a623be8d37e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406444"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="06694-102">CorpubPublish Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="06694-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="06694-103">Uygulama etki alanları ve işlemler hakkında bilgi yayımlamak için arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="06694-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06694-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06694-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="06694-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="06694-105">Interfaces</span></span>  
  
|<span data-ttu-id="06694-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="06694-106">Interface</span></span>|<span data-ttu-id="06694-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06694-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="06694-108">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06694-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="06694-109">Bu işlemleri süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="06694-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="06694-110">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06694-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="06694-111">Temsil eder ve bir işlemde bir uygulama etki alanı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="06694-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="06694-112">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06694-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="06694-113">Şu anda bir işlem içinde mevcut uygulama etki alanları koleksiyonu çapraz yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="06694-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="06694-114">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06694-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="06694-115">Bir bilgisayarda çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="06694-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="06694-116">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06694-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="06694-117">Bir bilgisayarda çalışan işlemlerin bir koleksiyon geçiş yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="06694-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06694-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06694-118">Remarks</span></span>  
 <span data-ttu-id="06694-119">Tipik bir yayımlama senaryosu uygulama etki alanı içindeki bir bilgisayarda çalışan yönetilen kodda hata ayıklama isteyen bir geliştirici içerir.</span><span class="sxs-lookup"><span data-stu-id="06694-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="06694-120">Barındırma ortamı birden fazla uygulama etki alanı bir işlem içinde çalışmıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="06694-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="06694-121">Geliştirici, tüm bilgisayar üzerinde çalışan işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir şekilde kullanmak ve belirli bir işlemin çekme ister misiniz?</span><span class="sxs-lookup"><span data-stu-id="06694-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="06694-122">Listenin tüm yönetilen kod çalışan işlemleri içinde uygulama etki alanları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="06694-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="06694-123">Geliştirici belirli uygulama etki alanını tanımlamak ve bir hata ayıklayıcı bu etki alanına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="06694-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06694-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06694-124">Requirements</span></span>  
 <span data-ttu-id="06694-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06694-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06694-126">**Başlık:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="06694-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="06694-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06694-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06694-128">**.NET framework sürümleri:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06694-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06694-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06694-129">See Also</span></span>  
 [<span data-ttu-id="06694-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="06694-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
