---
title: "Nasıl yapılır: yükleme ve kaldırma derlemeler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd52a1094dba16c7e1bcba5bface9e13747cd4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a><span data-ttu-id="cc68e-102">Nasıl yapılır: yükleme ve kaldırma derlemeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc68e-102">How to: Load and Unload Assemblies (Visual Basic)</span></span>
<span data-ttu-id="cc68e-103">Programınız tarafından başvurulan derlemelerin otomatik olarak derleme zamanında yüklenir, ancak çalışma zamanında geçerli uygulama etki alanına belirli derlemeleri yüklemeye mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cc68e-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="cc68e-104">Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanı yük derlemelerine](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="cc68e-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="cc68e-105">Tek bir derleme tüm içerdiği uygulama etki alanlarının kaldırmak için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="cc68e-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="cc68e-106">Derleme kapsamı dışında kalsa bile içerdiği tüm uygulama etki alanları kaldırılana kadar gerçek derleme dosyası yüklü kalır.</span><span class="sxs-lookup"><span data-stu-id="cc68e-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="cc68e-107">Bazı derlemeleri ancak diğer kaldırmak istiyorsanız, yeni bir uygulama etki alanı oluşturma, o etki alanı içinde kod yürütme ve o uygulama etki alanı yüklemeyi kaldırma göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="cc68e-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="cc68e-108">Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="cc68e-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="cc68e-109">Uygulama etki alanına bir derlemeyi yüklemek için</span><span class="sxs-lookup"><span data-stu-id="cc68e-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="cc68e-110">Bazı yük sınıflarda bulunan yöntemleri kullanma <xref:System.AppDomain> ve <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="cc68e-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="cc68e-111">Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanı yük derlemelerine](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="cc68e-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="cc68e-112">Uygulama etki alanını kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="cc68e-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="cc68e-113">Tek bir derleme tüm içerdiği uygulama etki alanlarının kaldırmak için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="cc68e-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="cc68e-114">Kullanım `Unload` yönteminden <xref:System.AppDomain> uygulama etki alanları kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="cc68e-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="cc68e-115">Daha fazla bilgi için bkz: [nasıl yapılır: uygulama etki alanını boşaltma](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="cc68e-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc68e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc68e-116">See Also</span></span>  
 [<span data-ttu-id="cc68e-117">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="cc68e-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="cc68e-118">Derlemeler ve Genel Derleme Önbelleği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc68e-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="cc68e-119">Nasıl yapılır: uygulama etki alanına derlemeler yükleme</span><span class="sxs-lookup"><span data-stu-id="cc68e-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
