---
title: 'Nasıl yapılır: Uygulama Etki Alanı Oluşturma'
description: .NET içinde uygulama etki alanı oluşturma konusunu inceleyin. Kişisel olarak yönetilecek derlemeleri yüklemek için bir uygulama etki alanı oluşturabilir veya kod yürütmek için bir tane oluşturabilirsiniz.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: 8e44e682f64854dbc0181b26f6ed3fa2905b7814
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104808"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="34b82-104">Nasıl yapılır: Uygulama Etki Alanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="34b82-104">How to: Create an Application Domain</span></span>
<span data-ttu-id="34b82-105">Ortak dil çalışma zamanı ana bilgisayarı, gerektiğinde uygulama etki alanlarını otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="34b82-105">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="34b82-106">Bununla birlikte, kendi uygulama etki alanlarınızı oluşturabilir ve bunları kişisel olarak yönetmek istediğiniz derlemelere yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34b82-106">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="34b82-107">Ayrıca, kodu yürütebileceğiniz uygulama etki alanları da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34b82-107">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="34b82-108">Sınıfında aşırı yüklenmiş **CreateDomain** yöntemlerinden birini kullanarak yeni bir uygulama etki alanı oluşturursunuz <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="34b82-108">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="34b82-109">Uygulama etki alanına bir ad verebilir ve bu ada göre başvuru yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34b82-109">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="34b82-110">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur, bu adı atar `MyDomain` ve ardından ana bilgisayar etki alanının adını ve yeni oluşturulan alt uygulama etki alanını konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="34b82-110">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34b82-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="34b82-111">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="34b82-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34b82-112">See also</span></span>

- [<span data-ttu-id="34b82-113">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="34b82-113">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="34b82-114">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="34b82-114">Using Application Domains</span></span>](use.md)
