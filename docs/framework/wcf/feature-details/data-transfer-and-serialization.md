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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41357c9a039414ac692bac69337b2963d5c6b341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-transfer-and-serialization"></a>Veri Aktarma ve Seri Hale Getirme
Bağlı bir sistemde, hizmetler ve istemcileri herhangi bir görevi gerçekleştirmek için veri Exchange'de bağlıdır. Bir hizmet veya istemci geliştirici olarak size ayrıca anlamalısınız nasıl [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] işlediği verileri ve veri seri hale getirme, verimli ve bakımını kolay uygulamaları oluşturmak için.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Hizmet sözleşmelerinde belirten veri aktarımı](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 Veri aktarımı Hizmetleri'nde temel kavramlarını açıklar.  
  
 [Veri sözleşmelerini kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 Hangi verilerin sözleşmeler açıklar olan ve oluşturma ve bunları kullanın.  
  
 [Veri sözleşmesi seri hale getirici](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 Nasıl verilerle serileştirmek yapılacağını açıklayan <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı veya tüm uzantısını <xref:System.Runtime.Serialization.XmlObjectSerializer> sınıfı.  
  
 [XmlSerializer sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Neden ve nasıl açıklanmaktadır kullanmak için <xref:System.Xml.Serialization.XmlSerializer> sınıfı, bir alternatif <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.  
  
 [İleti sözleşmeleri kullanılıyor](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 İleti sözleşmeleri nasıl SOAP iletilerine ince denetime izin açıklar.  
  
 [İleti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 İleti sınıfı özelliklerinin nasıl kullanılacağını açıklar.  
  
 [Filtreleme](../../../../docs/framework/wcf/feature-details/filtering.md)  
 Filtreleme, açıklar çeşitli ölçütleri temel alarak bir ileti öncesi işlenmesini sağlar.  
  
 [Büyük veri ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 Bir ikili dosya gibi büyük bir veri bloğunu göndermeyi açıklar.  
  
 [Veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 Veri aktarma ve seri hale getirme programlamada dikkat edilmesi gereken öğeleri açıklar.  
  
 [Veri aktarımı mimarisi genel bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 Veri aktarımı genel tasarımını görünümünü açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kodlayıcılar ve seri hale getiricileri genişletme](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [En iyi uygulamalar: Veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Hizmet sürümü oluşturma](../../../../docs/framework/wcf/service-versioning.md)
