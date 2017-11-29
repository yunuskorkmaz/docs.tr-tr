---
title: "CorpubPublish Ortak Sınıfı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorpubPublish Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorpubPublish
helpviewer_keywords: CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c1565c9321e64536139e02b239fbeb4247a58a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="fcc30-102">CorpubPublish Coclass’ı</span><span class="sxs-lookup"><span data-stu-id="fcc30-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="fcc30-103">Uygulama etki alanları ve işlemler hakkında bilgi yayımlamak için arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcc30-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcc30-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="fcc30-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="fcc30-105">Interfaces</span></span>  
  
|<span data-ttu-id="fcc30-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="fcc30-106">Interface</span></span>|<span data-ttu-id="fcc30-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcc30-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fcc30-108">Icorpublish arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcc30-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="fcc30-109">Bu işlemleri süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcc30-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="fcc30-110">Icorpublishappdomain arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcc30-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="fcc30-111">Temsil eder ve bir işlemde bir uygulama etki alanı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcc30-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="fcc30-112">Icorpublishappdomainenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcc30-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="fcc30-113">Şu anda bir işlem içinde mevcut uygulama etki alanları koleksiyonu çapraz yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcc30-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="fcc30-114">Icorpublishprocess arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcc30-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="fcc30-115">Bir bilgisayarda çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fcc30-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="fcc30-116">Icorpublishprocessenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcc30-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="fcc30-117">Bir bilgisayarda çalışan işlemlerin bir koleksiyon geçiş yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcc30-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcc30-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcc30-118">Remarks</span></span>  
 <span data-ttu-id="fcc30-119">Tipik bir yayımlama senaryosu uygulama etki alanı içindeki bir bilgisayarda çalışan yönetilen kodda hata ayıklama isteyen bir geliştirici içerir.</span><span class="sxs-lookup"><span data-stu-id="fcc30-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="fcc30-120">Barındırma ortamı birden fazla uygulama etki alanı bir işlem içinde çalışmıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="fcc30-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="fcc30-121">Geliştirici, tüm bilgisayar üzerinde çalışan işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir şekilde kullanmak ve belirli bir işlemin çekme ister misiniz?</span><span class="sxs-lookup"><span data-stu-id="fcc30-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="fcc30-122">Listenin tüm yönetilen kod çalışan işlemleri içinde uygulama etki alanları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="fcc30-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="fcc30-123">Geliştirici belirli uygulama etki alanını tanımlamak ve bir hata ayıklayıcı bu etki alanına bağlayın.</span><span class="sxs-lookup"><span data-stu-id="fcc30-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcc30-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcc30-124">Requirements</span></span>  
 <span data-ttu-id="fcc30-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcc30-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcc30-126">**Başlık:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="fcc30-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="fcc30-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcc30-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcc30-128">**.NET framework sürümleri:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcc30-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc30-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcc30-129">See Also</span></span>  
 [<span data-ttu-id="fcc30-130">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="fcc30-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
