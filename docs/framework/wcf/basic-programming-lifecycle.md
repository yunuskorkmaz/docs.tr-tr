---
title: "Temel Programlama Yaşam Döngüsü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f5c45cad0b1e4ae1aa6b1963e9acdab47cd9203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="eb7c9-102">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="eb7c9-102">Basic Programming Lifecycle</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="eb7c9-103">uygulamaların aynı bilgisayarda Internet üzerinden veya farklı bir uygulama platformlarda olup olmadıklarını iletişim kurmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-103"> enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="eb7c9-104">Derleme için gerekli görevleri bu konuda özetlenir bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-104">This topic outlines the tasks that are required to build a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="eb7c9-105">Çalışan bir örnek uygulama için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="eb7c9-105">For a working sample application, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="eb7c9-106">Basit görevler</span><span class="sxs-lookup"><span data-stu-id="eb7c9-106">The Basic Tasks</span></span>  
 <span data-ttu-id="eb7c9-107">Temel görevleri gerçekleştirmek için sırasıyla şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eb7c9-107">The basic tasks to perform are, in order:</span></span>  
  
1.  <span data-ttu-id="eb7c9-108">Hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-108">Define the service contract.</span></span> <span data-ttu-id="eb7c9-109">Bir hizmet sözleşmesini bir hizmet, bu alış verişleri veri ve diğer kapsamındaki gerekli verileri imzası belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="eb7c9-110">[Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="eb7c9-110"> [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="eb7c9-111">Sözleşme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-111">Implement the contract.</span></span> <span data-ttu-id="eb7c9-112">Bir hizmet sözleşmesini uygulama için sözleşme uygulayan bir sınıf oluşturun ve çalışma zamanı olmalıdır özel davranışlar belirtin.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="eb7c9-113">[Hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="eb7c9-113"> [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
3.  <span data-ttu-id="eb7c9-114">Hizmet uç noktaları ve diğer davranış bilgileri belirterek yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-114">Configure the service by specifying endpoints and other behavior information.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="eb7c9-115">[Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="eb7c9-115"> [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
4.  <span data-ttu-id="eb7c9-116">Hizmetini barındırır.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-116">Host the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="eb7c9-117">[Barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="eb7c9-117"> [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
5.  <span data-ttu-id="eb7c9-118">Bir istemci uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-118">Build a client application.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="eb7c9-119">[İstemcileri derleme](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="eb7c9-119"> [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
 <span data-ttu-id="eb7c9-120">Bu bölümdeki konular, bu sırada izleyin rağmen bazı senaryolar başında başlatmayın.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="eb7c9-121">Örneğin, önceden var olan bir hizmet için bir istemci oluşturmak istiyorsanız, adım 5 başlatın.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="eb7c9-122">Veya diğer kullanıcıların kullanacağı bir hizmet oluşturuluyorsa, adım 5 atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="eb7c9-123">Hizmet sözleşmelerini geliştirmeyi hakkında bilgi sahibi olduktan sonra ayrıca okuyabilirsiniz [genişletilebilirlik genel bakış](../../../docs/framework/wcf/introduction-to-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="eb7c9-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md).</span></span> <span data-ttu-id="eb7c9-124">Hizmetiniz ile ilgili sorununuz varsa, denetleyin [WCF sorun giderme Hızlı Başlangıç](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) başkalarının aynı veya benzer sorunlar yüklü olup olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7c9-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb7c9-125">See Also</span></span>  
 [<span data-ttu-id="eb7c9-126">Hizmet Anlaşmalarını Uygulama</span><span class="sxs-lookup"><span data-stu-id="eb7c9-126">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
