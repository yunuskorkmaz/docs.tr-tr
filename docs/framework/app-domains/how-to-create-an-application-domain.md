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
ms.openlocfilehash: 6f8d791a7aa673c25104e5dddf018d4b167563ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="68f11-102">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="68f11-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="68f11-103">Gerektiğinde bir ortak dil çalışma zamanı ana uygulama etki alanları otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="68f11-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="68f11-104">Ancak, kendi uygulama etki alanları oluşturmak ve bunlara kişisel yönetmek istediğiniz bu derlemeler yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="68f11-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="68f11-105">Uygulama etki alanları kod yürütmek de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68f11-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="68f11-106">Aşırı yüklenmiş birini kullanarak yeni bir uygulama etki alanı oluşturma **CreateDomain** yöntemleri <xref:System.AppDomain?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="68f11-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="68f11-107">Uygulama etki alanı bir ad verin ve bu adı referans.</span><span class="sxs-lookup"><span data-stu-id="68f11-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="68f11-108">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur, adı atar `MyDomain`ve adını ana etki alanı ve yeni oluşturulan alt uygulama etki alanı konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="68f11-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68f11-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="68f11-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="68f11-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68f11-110">See Also</span></span>  
 [<span data-ttu-id="68f11-111">Uygulama etki alanları ile programlama</span><span class="sxs-lookup"><span data-stu-id="68f11-111">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="68f11-112">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="68f11-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
