---
title: Temel Programlama Yaşam Döngüsü
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: fe578ba3c655c9c9ea8398b9b2e4d4f974153c8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320821"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="d2430-102">Temel Programlama Yaşam Döngüsü</span><span class="sxs-lookup"><span data-stu-id="d2430-102">Basic Programming Lifecycle</span></span>
<span data-ttu-id="d2430-103">Windows Communication Foundation (WCF), uygulamaların aynı bilgisayarda, Internet üzerinden veya farklı uygulama platformlarında olup olmadıkları ile iletişim kurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2430-103">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="d2430-104">Bu konu, bir WCF uygulaması oluşturmak için gereken görevleri özetler.</span><span class="sxs-lookup"><span data-stu-id="d2430-104">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="d2430-105">Çalışan bir örnek uygulama için bkz. [Başlangıç Öğreticisi](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="d2430-105">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="d2430-106">Temel görevler</span><span class="sxs-lookup"><span data-stu-id="d2430-106">The Basic Tasks</span></span>  
 <span data-ttu-id="d2430-107">Gerçekleştirilecek temel görevler sırasıyla:</span><span class="sxs-lookup"><span data-stu-id="d2430-107">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="d2430-108">Hizmet sözleşmesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d2430-108">Define the service contract.</span></span> <span data-ttu-id="d2430-109">Hizmet sözleşmesi bir hizmetin imzasını, yaptığı verileri ve diğer sözleşmeye dayalı gerekli verileri belirler.</span><span class="sxs-lookup"><span data-stu-id="d2430-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="d2430-110">Daha fazla bilgi için bkz. [hizmet sözleşmelerini tasarlama](designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d2430-110">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="d2430-111">Sözleşmeyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d2430-111">Implement the contract.</span></span> <span data-ttu-id="d2430-112">Bir hizmet sözleşmesi uygulamak için, sözleşmeyi uygulayan bir sınıf oluşturun ve çalışma zamanının sahip olduğu özel davranışları belirtin.</span><span class="sxs-lookup"><span data-stu-id="d2430-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="d2430-113">Daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d2430-113">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="d2430-114">Uç noktaları ve diğer davranış bilgilerini belirterek hizmeti yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d2430-114">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="d2430-115">Daha fazla bilgi için bkz. [Hizmetleri yapılandırma](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="d2430-115">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="d2430-116">Hizmeti barındırın.</span><span class="sxs-lookup"><span data-stu-id="d2430-116">Host the service.</span></span> <span data-ttu-id="d2430-117">Daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="d2430-117">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="d2430-118">Bir istemci uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d2430-118">Build a client application.</span></span> <span data-ttu-id="d2430-119">Daha fazla bilgi için bkz. [Istemcileri derleme](building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d2430-119">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="d2430-120">Bu bölümdeki konular bu sırayı takip etse de, bazı senaryolar başlangıcında başlamaz.</span><span class="sxs-lookup"><span data-stu-id="d2430-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="d2430-121">Örneğin, önceden var olan bir hizmet için istemci derlemek isterseniz 5. adımda başlar.</span><span class="sxs-lookup"><span data-stu-id="d2430-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="d2430-122">Veya başkalarının kullanacağı bir hizmet oluşturuyorsanız 5. adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2430-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="d2430-123">Hizmet sözleşmeleri geliştirmeye alışdıktan sonra, [genişletilebilirliğine giriş](introduction-to-extensibility.md)de okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2430-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="d2430-124">Hizmetinizdeki sorunlarla karşılaşırsanız, diğer kişilerin aynı veya benzer sorunlara sahip olup olmadığını görmek için [WCF sorun giderme hızlı](wcf-troubleshooting-quickstart.md) başlangıcı ' nı kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="d2430-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2430-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2430-125">See also</span></span>

- [<span data-ttu-id="d2430-126">Hizmet Anlaşmalarını Uygulama</span><span class="sxs-lookup"><span data-stu-id="d2430-126">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
