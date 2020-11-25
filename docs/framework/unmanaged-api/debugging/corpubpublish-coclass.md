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
ms.openlocfilehash: c73eab14bf6f9f9599bed79f4c5f85ed035c0518
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722355"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="1b7eb-102">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="1b7eb-102">CorpubPublish Coclass</span></span>

<span data-ttu-id="1b7eb-103">Uygulama etki alanları ve işlemleriyle ilgili bilgileri yayımlamak için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b7eb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b7eb-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="1b7eb-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="1b7eb-105">Interfaces</span></span>  
  
|<span data-ttu-id="1b7eb-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="1b7eb-106">Interface</span></span>|<span data-ttu-id="1b7eb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b7eb-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="1b7eb-108">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b7eb-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="1b7eb-109">Bu süreçlerdeki süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="1b7eb-110">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b7eb-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="1b7eb-111">, Bir işlemdeki uygulama etki alanı ile ilgili bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="1b7eb-112">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b7eb-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="1b7eb-113">Bir işlem içinde mevcut olan bir uygulama etki alanı koleksiyonunu gezme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="1b7eb-114">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b7eb-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="1b7eb-115">Bir bilgisayarda çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="1b7eb-116">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b7eb-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="1b7eb-117">Bir bilgisayarda çalışan işlem koleksiyonunda geçiş yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b7eb-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b7eb-118">Remarks</span></span>  

 <span data-ttu-id="1b7eb-119">Tipik bir yayımlama senaryosu, uygulama etki alanındaki bir bilgisayarda çalışan yönetilen kodda hata ayıklamak isteyen bir geliştirici içerir.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="1b7eb-120">Barındırma ortamı bir işlem içinde birden fazla uygulama etki alanı çalıştırıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="1b7eb-121">Geliştirici, bilgisayarda çalışan tüm işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir yöntem kullanmak ister ve belirli bir işlem seçer.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="1b7eb-122">Liste, yönetilen kod çalıştıran işlemlerin içindeki tüm uygulama etki alanlarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="1b7eb-123">Geliştirici daha sonra belirli uygulama etki alanını tanımlayabilir ve bu etki alanına bir hata ayıklayıcı ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b7eb-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b7eb-124">Requirements</span></span>  

 <span data-ttu-id="1b7eb-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b7eb-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b7eb-126">**Üst bilgi:** CorPub. IDL</span><span class="sxs-lookup"><span data-stu-id="1b7eb-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="1b7eb-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1b7eb-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b7eb-128">**.NET Framework sürümleri:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b7eb-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7eb-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b7eb-129">See also</span></span>

- [<span data-ttu-id="1b7eb-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1b7eb-130">Debugging</span></span>](index.md)
