---
title: "Nasıl yapılır: Uygulama Etki Alanı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e17b4d542206deadf960234cfe1091896ab5f92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="c0e6e-102">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0e6e-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="c0e6e-103">Gerektiğinde bir ortak dil çalışma zamanı ana uygulama etki alanları otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="c0e6e-104">Ancak, kendi uygulama etki alanları oluşturmak ve bunlara kişisel yönetmek istediğiniz bu derlemeler yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="c0e6e-105">Uygulama etki alanları kod yürütmek de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="c0e6e-106">Aşırı yüklenmiş birini kullanarak yeni bir uygulama etki alanı oluşturma **CreateDomain** yöntemleri <xref:System.AppDomain?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c0e6e-107">Uygulama etki alanı bir ad verin ve bu adı referans.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="c0e6e-108">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur, adı atar `MyDomain`ve adını ana etki alanı ve yeni oluşturulan alt uygulama etki alanı konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0e6e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0e6e-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c0e6e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-110">See Also</span></span>  
 [<span data-ttu-id="c0e6e-111">Uygulama etki alanları ile programlama</span><span class="sxs-lookup"><span data-stu-id="c0e6e-111">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="c0e6e-112">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="c0e6e-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
