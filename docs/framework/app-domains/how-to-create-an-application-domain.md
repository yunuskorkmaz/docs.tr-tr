---
title: 'Nasıl yapılır: Uygulama Etki Alanı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff85f5737babb73d87f4918ca0f4981263f7dadc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705720"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="81899-102">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="81899-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="81899-103">Gerektiğinde, bir ortak dil çalışma zamanı ana uygulama etki alanları otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="81899-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="81899-104">Ancak, kendi uygulama etki alanları oluşturmak ve bunlara kişisel yönetmek istediğiniz bu derlemeleri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="81899-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="81899-105">Ayrıca, kod yürütme uygulama etki alanları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81899-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="81899-106">Aşırı yüklenen birini kullanarak yeni bir uygulama etki alanı oluşturma **CreateDomain** yöntemleri <xref:System.AppDomain?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="81899-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="81899-107">Uygulama etki alanına bir ad verin ve bu adla başvurun.</span><span class="sxs-lookup"><span data-stu-id="81899-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="81899-108">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur, ad atar `MyDomain`ve ardından adını ana etki alanı ve yeni oluşturulan alt uygulama etki alanı konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="81899-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81899-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="81899-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="81899-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81899-110">See also</span></span>

- [<span data-ttu-id="81899-111">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="81899-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="81899-112">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="81899-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
