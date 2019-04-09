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
ms.openlocfilehash: 05d9eef36885aee05d88f7da994c8b168c3221b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130539"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="136e6-102">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="136e6-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="136e6-103">Uygulama etki alanları ve işlemler hakkında bilgi yayımlamak için arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="136e6-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="136e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="136e6-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="136e6-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="136e6-105">Interfaces</span></span>  
  
|<span data-ttu-id="136e6-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="136e6-106">Interface</span></span>|<span data-ttu-id="136e6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="136e6-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="136e6-108">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="136e6-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="136e6-109">Bu işlemde süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="136e6-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="136e6-110">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="136e6-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="136e6-111">Temsil eder ve bir uygulama etki alanında bir işlem hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="136e6-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="136e6-112">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="136e6-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="136e6-113">Şu anda bir işlem içinde varolan bir uygulama etki alanlarının bir koleksiyonu geçirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="136e6-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="136e6-114">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="136e6-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="136e6-115">Bir bilgisayar üzerinde çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="136e6-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="136e6-116">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="136e6-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="136e6-117">Bir bilgisayarda çalışan işlemler koleksiyonunu geçirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="136e6-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="136e6-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="136e6-118">Remarks</span></span>  
 <span data-ttu-id="136e6-119">Yayımlama için tipik senaryo, bir uygulama etki alanındaki bir bilgisayarda çalışan yönetilen kodda hata ayıklamak için isteyen bir geliştirici içerir.</span><span class="sxs-lookup"><span data-stu-id="136e6-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="136e6-120">Bir işlem içinde birden fazla uygulama etki alanı barındırma ortamı çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="136e6-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="136e6-121">Geliştirici, tüm bilgisayarda çalışan işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir yolla kullanın ve belirli bir işlem seçin ister misiniz?</span><span class="sxs-lookup"><span data-stu-id="136e6-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="136e6-122">Listenin tüm yönetilen kod çalışan işlemleri içinde uygulama etki alanları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="136e6-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="136e6-123">Geliştirici belirli bir uygulama etki alanını tanımlamak ve bir hata ayıklayıcı bu etki alanına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="136e6-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="136e6-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="136e6-124">Requirements</span></span>  
 <span data-ttu-id="136e6-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="136e6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="136e6-126">**Üst bilgi:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="136e6-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="136e6-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="136e6-127">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="136e6-128">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="136e6-128">.NET Framework Versions:</span></span>**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="136e6-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="136e6-129">See also</span></span>

- [<span data-ttu-id="136e6-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="136e6-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
