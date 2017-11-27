---
title: "Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ed6674580649e645ea3e647fa00682f2545255e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="5d17a-102">Bir Uygulama Etki Alanından Kurulum Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="5d17a-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="5d17a-103">Uygulama etki alanı her örneği her iki özellikten oluşur ve <xref:System.AppDomainSetup> bilgi.</span><span class="sxs-lookup"><span data-stu-id="5d17a-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="5d17a-104">Kullanarak bir uygulama etki alanı, Kur bilgi alabileceğiniz <xref:System.AppDomain?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5d17a-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5d17a-105">Bu sınıf, uygulama etki alanı hakkında yapılandırma bilgilerini almak birkaç üye sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d17a-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="5d17a-106">Sorgu da **AppDomainSetup** oluşturulduğunda, etki alanına geçirilen kurulum bilgilerini almak uygulama etki alanı için nesne.</span><span class="sxs-lookup"><span data-stu-id="5d17a-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="5d17a-107">Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur ve birkaç üyesine değerlerini konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5d17a-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="5d17a-108">Aşağıdaki örnek kümeleri ve alır, Kur bilgi için uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="5d17a-108">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="5d17a-109">Unutmayın `AppDomain.SetupInformation.ApplicationBase` yapılandırma bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="5d17a-109">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5d17a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d17a-110">See Also</span></span>  
 [<span data-ttu-id="5d17a-111">Uygulama etki alanları ile programlama</span><span class="sxs-lookup"><span data-stu-id="5d17a-111">Programming with Application Domains</span></span>](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="5d17a-112">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="5d17a-112">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
