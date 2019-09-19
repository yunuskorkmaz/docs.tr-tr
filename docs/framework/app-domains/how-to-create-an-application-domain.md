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
ms.openlocfilehash: 7f42f85adf3e9b0874df6c0360bea25b07facc0d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053154"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="934e5-102">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="934e5-102">How to: Create an Application Domain</span></span>
<span data-ttu-id="934e5-103">Ortak dil çalışma zamanı ana bilgisayarı, gerektiğinde uygulama etki alanlarını otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="934e5-103">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="934e5-104">Bununla birlikte, kendi uygulama etki alanlarınızı oluşturabilir ve bunları kişisel olarak yönetmek istediğiniz derlemelere yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="934e5-104">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="934e5-105">Ayrıca, kodu yürütebileceğiniz uygulama etki alanları da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="934e5-105">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="934e5-106"><xref:System.AppDomain?displayProperty=nameWithType> Sınıfında aşırı yüklenmiş **CreateDomain** yöntemlerinden birini kullanarak yeni bir uygulama etki alanı oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="934e5-106">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="934e5-107">Uygulama etki alanına bir ad verebilir ve bu ada göre başvuru yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="934e5-107">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="934e5-108">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur, bu adı `MyDomain`atar ve ardından ana bilgisayar etki alanının adını ve yeni oluşturulan alt uygulama etki alanını konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="934e5-108">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="934e5-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="934e5-109">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="934e5-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="934e5-110">See also</span></span>

- [<span data-ttu-id="934e5-111">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="934e5-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="934e5-112">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="934e5-112">Using Application Domains</span></span>](use.md)
