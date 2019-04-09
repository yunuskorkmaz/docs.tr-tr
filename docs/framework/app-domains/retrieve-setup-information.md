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
ms.openlocfilehash: 80c9fe6de0fca86497ffe84cd8dadf0eb8cef6c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108959"
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="cab3a-102">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="cab3a-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="cab3a-103">Her örnek bir uygulama etki alanının her iki özellikten oluşur ve <xref:System.AppDomainSetup> bilgileri.</span><span class="sxs-lookup"><span data-stu-id="cab3a-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="cab3a-104">Kullanarak bir uygulama etki alanı kurulum bilgilerini alabilir <xref:System.AppDomain?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cab3a-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="cab3a-105">Bu sınıf, bir uygulama etki alanı yapılandırma bilgilerini almak birkaç üyeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cab3a-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="cab3a-106">Ayrıca Sorgulayabileceğiniz **AppDomainSetup** oluşturulduğunda, etki alanına geçirildi kurulum bilgilerini almak uygulama etki alanı için nesne.</span><span class="sxs-lookup"><span data-stu-id="cab3a-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="cab3a-107">Aşağıdaki örnek, yeni bir uygulama etki alanı oluşturur ve ardından çeşitli üye değerleri konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cab3a-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="cab3a-108">Örnek ayarlar ve alır, kurulum için aşağıdaki bilgileri uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="cab3a-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="cab3a-109">Unutmayın `AppDomain.SetupInformation.ApplicationBase` yapılandırma bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="cab3a-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="cab3a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cab3a-110">See also</span></span>

- [<span data-ttu-id="cab3a-111">Uygulama Etki Alanlarıyla Programlama</span><span class="sxs-lookup"><span data-stu-id="cab3a-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="cab3a-112">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="cab3a-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
