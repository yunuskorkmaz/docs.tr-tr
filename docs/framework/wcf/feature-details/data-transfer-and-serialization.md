---
title: Veri Aktarma ve Seri Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 1eefd82a149d0bc215ca441e92c7d737a744b1e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088411"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="aa8ce-102">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="aa8ce-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="aa8ce-103">Bağlı bir sistemde, hizmetler ve istemcileri üzerinde herhangi bir görevi tamamlamak için veri alışverişi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="aa8ce-104">Bir hizmet veya istemci bir geliştirici olarak, Windows Communication Foundation (WCF) veri ve veri seri hale getirme verimli ve sürdürmek daha kolay olan uygulamalar oluşturmak için işleme biçimini de anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa8ce-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="aa8ce-105">In This Section</span></span>  
 [<span data-ttu-id="aa8ce-106">Hizmet Sözleşmelerinde Veri Aktarımını Belirtme</span><span class="sxs-lookup"><span data-stu-id="aa8ce-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="aa8ce-107">Veri aktarımı Hizmetleri temel kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="aa8ce-108">Veri Sözleşmelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="aa8ce-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="aa8ce-109">Hangi veri sözleşmeleri açıklar olan ve oluşturma ve bunları kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="aa8ce-110">Veri Sözleşmesi Seri Hale Getirici</span><span class="sxs-lookup"><span data-stu-id="aa8ce-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="aa8ce-111">Verilerle serileştirmek nasıl yapılacağını anlatmaktadır <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı veya herhangi bir uzantısına <xref:System.Runtime.Serialization.XmlObjectSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="aa8ce-112">XmlSerializer Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="aa8ce-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="aa8ce-113">Neden ve nasıl açıklar kullanılacak <xref:System.Xml.Serialization.XmlSerializer> sınıfı, alternatif <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="aa8ce-114">İleti Sözleşmeleri Kullanılıyor</span><span class="sxs-lookup"><span data-stu-id="aa8ce-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="aa8ce-115">İleti sözleşmeleri SOAP iletilerini üzerinde ayrıntılı denetim nasıl izin açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="aa8ce-116">İleti Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="aa8ce-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="aa8ce-117">İleti sınıfı özelliklerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="aa8ce-118">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="aa8ce-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="aa8ce-119">Filtreleme, açıklayan bir iletinin çeşitli ölçütleri temel alarak ön işleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="aa8ce-120">Büyük Veriler ve Akış Yapma</span><span class="sxs-lookup"><span data-stu-id="aa8ce-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="aa8ce-121">İkili dosyaları gibi büyük bir veri bloğunu göndermeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="aa8ce-122">Veriler için Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="aa8ce-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="aa8ce-123">Veri aktarımı ve Serileştirme programlamada dikkat edilmesi gereken öğeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="aa8ce-124">Veri Aktarımı Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aa8ce-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="aa8ce-125">WCF veri aktarımı Genel Tasarım görünümünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aa8ce-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="aa8ce-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="aa8ce-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="aa8ce-127">Related Sections</span></span>  
 [<span data-ttu-id="aa8ce-128">Kodlayıcılar ve Seri Hale Getiricileri Genişletme</span><span class="sxs-lookup"><span data-stu-id="aa8ce-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="aa8ce-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa8ce-129">See also</span></span>

- [<span data-ttu-id="aa8ce-130">En İyi Yöntemler: Veri Sözleşmesi Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa8ce-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [<span data-ttu-id="aa8ce-131">Hizmet Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa8ce-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
