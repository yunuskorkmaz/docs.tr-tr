---
title: Veri Aktarma ve Seri Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 53c1421bf14c598611e116c61353c4ecd465f1aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489212"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="7473d-102">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="7473d-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="7473d-103">Bağlı bir sistemde, hizmetler ve istemcileri herhangi bir görevi gerçekleştirmek için veri Exchange'de bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7473d-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="7473d-104">Bir hizmet veya istemci geliştiricisi olarak, Windows Communication Foundation (WCF) veri ve veri seri hale getirme, verimli ve bakımını kolay uygulamaları oluşturmak için işleme biçimini anlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="7473d-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7473d-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7473d-105">In This Section</span></span>  
 [<span data-ttu-id="7473d-106">Hizmet Anlaşmalarında Veri Aktarımını Belirtme</span><span class="sxs-lookup"><span data-stu-id="7473d-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="7473d-107">Veri aktarımı Hizmetleri'nde temel kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7473d-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="7473d-108">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="7473d-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="7473d-109">Hangi verilerin sözleşmeler açıklar olan ve oluşturma ve bunları kullanın.</span><span class="sxs-lookup"><span data-stu-id="7473d-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="7473d-110">Veri Anlaşması Seri Hale Getirici</span><span class="sxs-lookup"><span data-stu-id="7473d-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="7473d-111">Nasıl verilerle serileştirmek yapılacağını açıklayan <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı veya tüm uzantısını <xref:System.Runtime.Serialization.XmlObjectSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7473d-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="7473d-112">XmlSerializer Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="7473d-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="7473d-113">Neden ve nasıl açıklanmaktadır kullanmak için <xref:System.Xml.Serialization.XmlSerializer> sınıfı, bir alternatif <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7473d-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="7473d-114">İleti Anlaşmaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="7473d-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="7473d-115">İleti sözleşmeleri nasıl SOAP iletilerine ince denetime izin açıklar.</span><span class="sxs-lookup"><span data-stu-id="7473d-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="7473d-116">İleti Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="7473d-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="7473d-117">İleti sınıfı özelliklerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7473d-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="7473d-118">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="7473d-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="7473d-119">Filtreleme, açıklar çeşitli ölçütleri temel alarak bir ileti öncesi işlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7473d-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="7473d-120">Büyük Veriler ve Akış Yapma</span><span class="sxs-lookup"><span data-stu-id="7473d-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="7473d-121">Bir ikili dosya gibi büyük bir veri bloğunu göndermeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7473d-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="7473d-122">Veriler için Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="7473d-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="7473d-123">Veri aktarma ve seri hale getirme programlamada dikkat edilmesi gereken öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="7473d-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="7473d-124">Veri Aktarımı Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7473d-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="7473d-125">WCF veri aktarımı genel tasarımını görünümünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="7473d-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7473d-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7473d-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="7473d-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7473d-127">Related Sections</span></span>  
 [<span data-ttu-id="7473d-128">Kodlayıcılar ve Seri Hale Getiricileri Genişletme</span><span class="sxs-lookup"><span data-stu-id="7473d-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="7473d-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7473d-129">See Also</span></span>  
 [<span data-ttu-id="7473d-130">En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7473d-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [<span data-ttu-id="7473d-131">Hizmet Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7473d-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
