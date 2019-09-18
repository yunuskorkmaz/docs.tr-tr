---
title: Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 719ea15de135d8bbeb7bb88ea3d5b5874e30b5d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053099"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="1ea0f-102">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="1ea0f-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="1ea0f-103">Bir uygulama etki alanının her örneği, hem özelliklerden <xref:System.AppDomainSetup> hem de bilgilerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1ea0f-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="1ea0f-104">Bir uygulama etki alanından kurulum bilgilerini <xref:System.AppDomain?displayProperty=nameWithType> sınıfını kullanarak alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ea0f-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="1ea0f-105">Bu sınıf, bir uygulama etki alanı hakkında yapılandırma bilgilerini alan çeşitli Üyeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ea0f-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="1ea0f-106">Ayrıca, uygulama etki alanı için **AppDomainSetup** nesnesini sorgulayabilirsiniz. Bu, etki alanına gönderilen kurulum bilgilerini elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="1ea0f-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="1ea0f-107">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur ve ardından konsola birkaç üye değeri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1ea0f-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="1ea0f-108">Aşağıdaki örnek, bir uygulama etki alanı için kurulum bilgilerini ayarlar ve ardından alır.</span><span class="sxs-lookup"><span data-stu-id="1ea0f-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="1ea0f-109">Yapılandırma bilgilerini `AppDomain.SetupInformation.ApplicationBase` alır.</span><span class="sxs-lookup"><span data-stu-id="1ea0f-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1ea0f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ea0f-110">See also</span></span>

- [<span data-ttu-id="1ea0f-111">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="1ea0f-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="1ea0f-112">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1ea0f-112">Using Application Domains</span></span>](use.md)
