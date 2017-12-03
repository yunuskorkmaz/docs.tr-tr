---
title: Veri Aktarma ve Seri Hale Getirme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29ca4041e24a99546dfb665b0ce9e695732442d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="88e18-102">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="88e18-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="88e18-103">Bağlı bir sistemde, hizmetler ve istemcileri herhangi bir görevi gerçekleştirmek için veri Exchange'de bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="88e18-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="88e18-104">Bir hizmet veya istemci geliştirici olarak size ayrıca anlamalısınız nasıl [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] işlediği verileri ve veri seri hale getirme, verimli ve bakımını kolay uygulamaları oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="88e18-104">As a developer of a service or client, you must also understand how [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88e18-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="88e18-105">In This Section</span></span>  
 [<span data-ttu-id="88e18-106">Hizmet sözleşmelerinde belirten veri aktarımı</span><span class="sxs-lookup"><span data-stu-id="88e18-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="88e18-107">Veri aktarımı Hizmetleri'nde temel kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="88e18-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="88e18-108">Veri sözleşmelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="88e18-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="88e18-109">Hangi verilerin sözleşmeler açıklar olan ve oluşturma ve bunları kullanın.</span><span class="sxs-lookup"><span data-stu-id="88e18-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="88e18-110">Veri sözleşmesi seri hale getirici</span><span class="sxs-lookup"><span data-stu-id="88e18-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="88e18-111">Nasıl verilerle serileştirmek yapılacağını açıklayan <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı veya tüm uzantısını <xref:System.Runtime.Serialization.XmlObjectSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88e18-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="88e18-112">XmlSerializer sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="88e18-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="88e18-113">Neden ve nasıl açıklanmaktadır kullanmak için <xref:System.Xml.Serialization.XmlSerializer> sınıfı, bir alternatif <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88e18-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="88e18-114">İleti sözleşmeleri kullanılıyor</span><span class="sxs-lookup"><span data-stu-id="88e18-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="88e18-115">İleti sözleşmeleri nasıl SOAP iletilerine ince denetime izin açıklar.</span><span class="sxs-lookup"><span data-stu-id="88e18-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="88e18-116">İleti sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="88e18-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="88e18-117">İleti sınıfı özelliklerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="88e18-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="88e18-118">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="88e18-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="88e18-119">Filtreleme, açıklar çeşitli ölçütleri temel alarak bir ileti öncesi işlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="88e18-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="88e18-120">Büyük veri ve akış</span><span class="sxs-lookup"><span data-stu-id="88e18-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="88e18-121">Bir ikili dosya gibi büyük bir veri bloğunu göndermeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="88e18-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="88e18-122">Veriler için güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="88e18-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="88e18-123">Veri aktarma ve seri hale getirme programlamada dikkat edilmesi gereken öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="88e18-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="88e18-124">Veri aktarımı mimarisi genel bakış</span><span class="sxs-lookup"><span data-stu-id="88e18-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="88e18-125">Veri aktarımı genel tasarımını görünümünü açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="88e18-125">Describes a view of the overall design of data transfer in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="88e18-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="88e18-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="88e18-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="88e18-127">Related Sections</span></span>  
 [<span data-ttu-id="88e18-128">Kodlayıcılar ve seri hale getiricileri genişletme</span><span class="sxs-lookup"><span data-stu-id="88e18-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="88e18-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88e18-129">See Also</span></span>  
 [<span data-ttu-id="88e18-130">En iyi uygulamalar: Veri sözleşmesi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="88e18-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [<span data-ttu-id="88e18-131">Hizmet sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="88e18-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
