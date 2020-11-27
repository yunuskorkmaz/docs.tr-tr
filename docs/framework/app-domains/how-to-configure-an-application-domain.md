---
title: 'Nasıl yapılır: Uygulama Etki Alanını Yapılandırma'
description: .NET ' te bir uygulama etki alanı yapılandırın. AppDomainSetup sınıfını kullanarak yeni bir uygulama etki alanı için CLR 'yi yapılandırma bilgileriyle sağlayabilirsiniz.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
ms.openlocfilehash: bbda1f75da6b994c54cd71c56f16615a3758859b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271518"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="c2d5f-104">Nasıl yapılır: Uygulama Etki Alanını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c2d5f-104">How to: Configure an Application Domain</span></span>

<span data-ttu-id="c2d5f-105">Sınıfını kullanarak yeni bir uygulama etki alanı için yapılandırma bilgileriyle ortak dil çalışma zamanı sağlayabilirsiniz <xref:System.AppDomainSetup> .</span><span class="sxs-lookup"><span data-stu-id="c2d5f-105">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="c2d5f-106">Kendi uygulama etki alanlarınızı oluştururken en önemli özellik ' dir <xref:System.AppDomainSetup.ApplicationBase%2A> .</span><span class="sxs-lookup"><span data-stu-id="c2d5f-106">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="c2d5f-107">Diğer **AppDomainSetup** özellikleri, genellikle belirli bir uygulama etki alanını yapılandırmak için çalışma zamanı konakları tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2d5f-107">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="c2d5f-108">**ApplicationBase** özelliği, uygulamanın kök dizinini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c2d5f-108">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="c2d5f-109">Çalışma zamanının bir tür isteğini karşılaması gerektiğinde, **ApplicationBase** özelliği tarafından belirtilen dizinde türü içeren derlemeyi yoklamalar.</span><span class="sxs-lookup"><span data-stu-id="c2d5f-109">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2d5f-110">Yeni bir uygulama etki alanı, oluşturucunun yalnızca **ApplicationBase** özelliğini devralır.</span><span class="sxs-lookup"><span data-stu-id="c2d5f-110">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="c2d5f-111">Aşağıdaki örnek, **AppDomainSetup** sınıfının bir örneğini oluşturur, yeni bir uygulama etki alanı oluşturmak için bu sınıfı kullanır, bilgileri konsola yazar ve ardından uygulama etki alanını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c2d5f-111">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2d5f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2d5f-112">Example</span></span>  

 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c2d5f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2d5f-113">See also</span></span>

- [<span data-ttu-id="c2d5f-114">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="c2d5f-114">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="c2d5f-115">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="c2d5f-115">Using Application Domains</span></span>](use.md)
