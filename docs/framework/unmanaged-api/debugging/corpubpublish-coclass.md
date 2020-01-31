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
ms.openlocfilehash: 24d245bbb0f9ac86e321491e0af3b66b1e011baa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789212"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="f79c1-102">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="f79c1-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="f79c1-103">Uygulama etki alanları ve işlemleriyle ilgili bilgileri yayımlamak için arabirimler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f79c1-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f79c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f79c1-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="f79c1-105">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f79c1-105">Interfaces</span></span>  
  
|<span data-ttu-id="f79c1-106">Arabirim</span><span class="sxs-lookup"><span data-stu-id="f79c1-106">Interface</span></span>|<span data-ttu-id="f79c1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f79c1-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="f79c1-108">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f79c1-108">ICorPublish Interface</span></span>](icorpublish-interface.md)|<span data-ttu-id="f79c1-109">Bu süreçlerdeki süreçler ve uygulama etki alanları hakkında bilgi yayımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f79c1-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="f79c1-110">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f79c1-110">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)|<span data-ttu-id="f79c1-111">, Bir işlemdeki uygulama etki alanı ile ilgili bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f79c1-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="f79c1-112">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f79c1-112">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)|<span data-ttu-id="f79c1-113">Bir işlem içinde mevcut olan bir uygulama etki alanı koleksiyonunu gezme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f79c1-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="f79c1-114">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f79c1-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)|<span data-ttu-id="f79c1-115">Bir bilgisayarda çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f79c1-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="f79c1-116">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f79c1-116">ICorPublishProcessEnum Interface</span></span>](icorpublishprocessenum-interface.md)|<span data-ttu-id="f79c1-117">Bir bilgisayarda çalışan işlem koleksiyonunda geçiş yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f79c1-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f79c1-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f79c1-118">Remarks</span></span>  
 <span data-ttu-id="f79c1-119">Tipik bir yayımlama senaryosu, uygulama etki alanındaki bir bilgisayarda çalışan yönetilen kodda hata ayıklamak isteyen bir geliştirici içerir.</span><span class="sxs-lookup"><span data-stu-id="f79c1-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="f79c1-120">Barındırma ortamı bir işlem içinde birden fazla uygulama etki alanı çalıştırıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f79c1-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="f79c1-121">Geliştirici, bilgisayarda çalışan tüm işlemleri listelemek için bir grafik kullanıcı arabirimi veya başka bir yöntem kullanmak ister ve belirli bir işlem seçer.</span><span class="sxs-lookup"><span data-stu-id="f79c1-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="f79c1-122">Liste, yönetilen kod çalıştıran işlemlerin içindeki tüm uygulama etki alanlarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f79c1-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="f79c1-123">Geliştirici daha sonra belirli uygulama etki alanını tanımlayabilir ve bu etki alanına bir hata ayıklayıcı ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f79c1-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f79c1-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f79c1-124">Requirements</span></span>  
 <span data-ttu-id="f79c1-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f79c1-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f79c1-126">**Üst bilgi:** CorPub. IDL</span><span class="sxs-lookup"><span data-stu-id="f79c1-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="f79c1-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f79c1-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f79c1-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f79c1-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f79c1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f79c1-129">See also</span></span>

- [<span data-ttu-id="f79c1-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f79c1-130">Debugging</span></span>](index.md)
