---
title: Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma
description: System. AppDomain sınıfını veya AppDomainSetup nesnesini kullanarak .NET 'teki bir uygulama etki alanından kurulum bilgilerini alın.
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
ms.openlocfilehash: 06bf6b5901736b87852492f48a9d8972490b8304
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903473"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="ba96e-103">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="ba96e-103">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="ba96e-104">Bir uygulama etki alanının her örneği, hem özelliklerden hem de <xref:System.AppDomainSetup> bilgilerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ba96e-104">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="ba96e-105">Bir uygulama etki alanından kurulum bilgilerini sınıfını kullanarak alabilirsiniz <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ba96e-105">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ba96e-106">Bu sınıf, bir uygulama etki alanı hakkında yapılandırma bilgilerini alan çeşitli Üyeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba96e-106">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="ba96e-107">Ayrıca, uygulama etki alanı için **AppDomainSetup** nesnesini sorgulayabilirsiniz. Bu, etki alanına gönderilen kurulum bilgilerini elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="ba96e-107">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="ba96e-108">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur ve ardından konsola birkaç üye değeri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ba96e-108">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="ba96e-109">Aşağıdaki örnek, bir uygulama etki alanı için kurulum bilgilerini ayarlar ve ardından alır.</span><span class="sxs-lookup"><span data-stu-id="ba96e-109">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="ba96e-110">`AppDomain.SetupInformation.ApplicationBase`Yapılandırma bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="ba96e-110">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ba96e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba96e-111">See also</span></span>

- [<span data-ttu-id="ba96e-112">Uygulama etki alanlarıyla programlama</span><span class="sxs-lookup"><span data-stu-id="ba96e-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="ba96e-113">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="ba96e-113">Using Application Domains</span></span>](use.md)
