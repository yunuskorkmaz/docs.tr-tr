---
title: 'Nasıl yapılır: Uygulama Etki Alanını Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 012f0220afa0e444d68af5998fb2492a03a371d8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183171"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="70ce4-102">Nasıl yapılır: Uygulama Etki Alanını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="70ce4-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="70ce4-103">Ortak dil çalışma zamanı kullanarak yeni bir uygulama etki alanı için yapılandırma bilgilerini sağlayabilir <xref:System.AppDomainSetup> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="70ce4-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="70ce4-104">Kendi uygulama etki alanları oluştururken, en önemli özelliği <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="70ce4-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="70ce4-105">Diğer **AppDomainSetup** özellikleri, belirli bir uygulama etki alanını yapılandırmak için temel olarak çalışma zamanı ana bilgisayarları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="70ce4-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="70ce4-106">**ApplicationBase** uygulamanın kök dizin özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70ce4-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="70ce4-107">Çalışma zamanı türü isteği karşılamak gerektiğinde türü tarafından belirtilen dizindeki içeren derleme yoklamaları **ApplicationBase** özelliği.</span><span class="sxs-lookup"><span data-stu-id="70ce4-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70ce4-108">Yeni bir uygulama etki alanı yalnızca devralınan **ApplicationBase** Oluşturucusu özelliği.</span><span class="sxs-lookup"><span data-stu-id="70ce4-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="70ce4-109">Aşağıdaki örnek, bir örneğini oluşturur. **AppDomainSetup** sınıfının yeni bir uygulama etki alanı oluşturmak için bu sınıfın kullandığı, bilgileri konsola yazar ve ardından uygulama etki alanını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="70ce4-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70ce4-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="70ce4-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="70ce4-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70ce4-111">See Also</span></span>  
- [<span data-ttu-id="70ce4-112">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="70ce4-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
- [<span data-ttu-id="70ce4-113">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="70ce4-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
