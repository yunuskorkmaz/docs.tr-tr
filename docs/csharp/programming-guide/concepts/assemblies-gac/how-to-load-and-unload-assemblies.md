---
title: "Nasıl yapılır: yük derlemeleri ve yüklemelerini kaldırma (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4b7c9e257a1fff6236770ff39f5d26cd97224b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-c"></a><span data-ttu-id="46b23-102">Nasıl yapılır: yük derlemeleri ve yüklemelerini kaldırma (C#)</span><span class="sxs-lookup"><span data-stu-id="46b23-102">How to: Load and Unload Assemblies (C#)</span></span>
<span data-ttu-id="46b23-103">Programınız tarafından başvurulan derlemelerin otomatik olarak derleme zamanında yüklenir, ancak çalışma zamanında geçerli uygulama etki alanına belirli derlemeleri yüklemeye mümkündür.</span><span class="sxs-lookup"><span data-stu-id="46b23-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="46b23-104">Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanı yük derlemelerine](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="46b23-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="46b23-105">Tek bir derleme tüm içerdiği uygulama etki alanlarının kaldırmak için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="46b23-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="46b23-106">Derleme kapsamı dışında kalsa bile içerdiği tüm uygulama etki alanları kaldırılana kadar gerçek derleme dosyası yüklü kalır.</span><span class="sxs-lookup"><span data-stu-id="46b23-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="46b23-107">Bazı derlemeleri ancak diğer kaldırmak istiyorsanız, yeni bir uygulama etki alanı oluşturma, o etki alanı içinde kod yürütme ve o uygulama etki alanı yüklemeyi kaldırma göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="46b23-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="46b23-108">Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="46b23-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="46b23-109">Uygulama etki alanına bir derlemeyi yüklemek için</span><span class="sxs-lookup"><span data-stu-id="46b23-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="46b23-110">Bazı yük sınıflarda bulunan yöntemleri kullanma <xref:System.AppDomain> ve <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="46b23-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="46b23-111">Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanı yük derlemelerine](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="46b23-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="46b23-112">Uygulama etki alanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="46b23-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="46b23-113">Tek bir derleme tüm içerdiği uygulama etki alanlarının kaldırmak için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="46b23-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="46b23-114">Kullanım `Unload` yönteminden <xref:System.AppDomain> uygulama etki alanları kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="46b23-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="46b23-115">Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="46b23-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b23-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46b23-116">See Also</span></span>  
 [<span data-ttu-id="46b23-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="46b23-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46b23-118">Derlemeler ve Genel Derleme Önbelleği (C#)</span><span class="sxs-lookup"><span data-stu-id="46b23-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="46b23-119">Nasıl yapılır: uygulama etki alanına derlemeler yükleme</span><span class="sxs-lookup"><span data-stu-id="46b23-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
