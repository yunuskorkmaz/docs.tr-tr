---
description: 'Daha fazla bilgi edinin: CorpubPublish coclass'
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
ms.openlocfilehash: fdf4be6ff2d20391e989998cd0045ed27d602561
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661707"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="640ae-103">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="640ae-103">CorpubPublish Coclass</span></span>

<span data-ttu-id="640ae-104">Uygulama etki alanları ve işlemleriyle ilgili bilgileri yayımlamak için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="640ae-104">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="640ae-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="640ae-105">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="640ae-106">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="640ae-106">Interfaces</span></span>  
  
|<span data-ttu-id="640ae-107">Arabirim</span><span class="sxs-lookup"><span data-stu-id="640ae-107">Interface</span></span>|<span data-ttu-id="640ae-108">Description</span><span class="sxs-lookup"><span data-stu-id="640ae-108">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="640ae-109">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640ae-109">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="640ae-110">Bu süreçlerdeki süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="640ae-110">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="640ae-111">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640ae-111">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="640ae-112">, Bir işlemdeki uygulama etki alanı ile ilgili bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="640ae-112">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="640ae-113">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640ae-113">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="640ae-114">Bir işlem içinde mevcut olan bir uygulama etki alanı koleksiyonunu gezme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="640ae-114">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="640ae-115">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640ae-115">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="640ae-116">Bir bilgisayarda çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="640ae-116">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="640ae-117">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="640ae-117">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="640ae-118">Bir bilgisayarda çalışan işlem koleksiyonunda geçiş yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="640ae-118">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="640ae-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="640ae-119">Remarks</span></span>  

 <span data-ttu-id="640ae-120">Tipik bir yayımlama senaryosu, uygulama etki alanındaki bir bilgisayarda çalışan yönetilen kodda hata ayıklamak isteyen bir geliştirici içerir.</span><span class="sxs-lookup"><span data-stu-id="640ae-120">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="640ae-121">Barındırma ortamı bir işlem içinde birden fazla uygulama etki alanı çalıştırıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="640ae-121">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="640ae-122">Geliştirici, bilgisayarda çalışan tüm işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir yöntem kullanmak ister ve belirli bir işlem seçer.</span><span class="sxs-lookup"><span data-stu-id="640ae-122">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="640ae-123">Liste, yönetilen kod çalıştıran işlemlerin içindeki tüm uygulama etki alanlarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="640ae-123">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="640ae-124">Geliştirici daha sonra belirli uygulama etki alanını tanımlayabilir ve bu etki alanına bir hata ayıklayıcı ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="640ae-124">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="640ae-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="640ae-125">Requirements</span></span>  

 <span data-ttu-id="640ae-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="640ae-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="640ae-127">**Üst bilgi:** CorPub. IDL</span><span class="sxs-lookup"><span data-stu-id="640ae-127">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="640ae-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="640ae-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="640ae-129">**.NET Framework sürümleri:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="640ae-129">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="640ae-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="640ae-130">See also</span></span>

- [<span data-ttu-id="640ae-131">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="640ae-131">Debugging</span></span>](index.md)
