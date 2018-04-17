---
title: Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5a7585b68c36fe5e435e563729d9a0f3540a42a
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="c26cb-102">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="c26cb-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="c26cb-103">Uygulama etki alanı her örneği her iki özellikten oluşur ve <xref:System.AppDomainSetup> bilgi.</span><span class="sxs-lookup"><span data-stu-id="c26cb-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="c26cb-104">Kullanarak bir uygulama etki alanı, Kur bilgi alabileceğiniz <xref:System.AppDomain?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c26cb-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c26cb-105">Bu sınıf, uygulama etki alanı hakkında yapılandırma bilgilerini almak birkaç üye sağlar.</span><span class="sxs-lookup"><span data-stu-id="c26cb-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="c26cb-106">Sorgu da **AppDomainSetup** oluşturulduğunda, etki alanına geçirilen kurulum bilgilerini almak uygulama etki alanı için nesne.</span><span class="sxs-lookup"><span data-stu-id="c26cb-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="c26cb-107">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur ve birkaç üyesine değerlerini konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c26cb-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="c26cb-108">Aşağıdaki örnek kümeleri ve alır, Kur bilgi için uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="c26cb-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="c26cb-109">Unutmayın `AppDomain.SetupInformation.ApplicationBase` yapılandırma bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="c26cb-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c26cb-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c26cb-110">See Also</span></span>  
 [<span data-ttu-id="c26cb-111">Uygulama etki alanları ile programlama</span><span class="sxs-lookup"><span data-stu-id="c26cb-111">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="c26cb-112">Uygulama Etki Alanlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="c26cb-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
