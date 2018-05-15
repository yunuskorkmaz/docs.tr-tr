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
ms.openlocfilehash: 6fab54080a529a9b5a93c06a4f249a9c14ecd7af
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="e112b-102">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="e112b-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="e112b-103">Uygulama etki alanı her örneği her iki özellikten oluşur ve <xref:System.AppDomainSetup> bilgi.</span><span class="sxs-lookup"><span data-stu-id="e112b-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="e112b-104">Kullanarak bir uygulama etki alanı, Kur bilgi alabileceğiniz <xref:System.AppDomain?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e112b-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e112b-105">Bu sınıf, uygulama etki alanı hakkında yapılandırma bilgilerini almak birkaç üye sağlar.</span><span class="sxs-lookup"><span data-stu-id="e112b-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="e112b-106">Sorgu da **AppDomainSetup** oluşturulduğunda, etki alanına geçirilen kurulum bilgilerini almak uygulama etki alanı için nesne.</span><span class="sxs-lookup"><span data-stu-id="e112b-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="e112b-107">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur ve birkaç üyesine değerlerini konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e112b-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="e112b-108">Aşağıdaki örnek kümeleri ve alır, Kur bilgi için uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="e112b-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="e112b-109">Unutmayın `AppDomain.SetupInformation.ApplicationBase` yapılandırma bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e112b-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e112b-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e112b-110">See Also</span></span>  
 [<span data-ttu-id="e112b-111">Uygulama etki alanları ile programlama</span><span class="sxs-lookup"><span data-stu-id="e112b-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="e112b-112">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e112b-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
