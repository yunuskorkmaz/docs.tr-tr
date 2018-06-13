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
# <a name="data-transfer-and-serialization"></a>Veri Aktarma ve Seri Hale Getirme
Bağlı bir sistemde, hizmetler ve istemcileri herhangi bir görevi gerçekleştirmek için veri Exchange'de bağlıdır. Bir hizmet veya istemci geliştiricisi olarak, Windows Communication Foundation (WCF) veri ve veri seri hale getirme, verimli ve bakımını kolay uygulamaları oluşturmak için işleme biçimini anlamalısınız.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 Veri aktarımı Hizmetleri'nde temel kavramlarını açıklar.  
  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 Hangi verilerin sözleşmeler açıklar olan ve oluşturma ve bunları kullanın.  
  
 [Veri Anlaşması Seri Hale Getirici](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 Nasıl verilerle serileştirmek yapılacağını açıklayan <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı veya tüm uzantısını <xref:System.Runtime.Serialization.XmlObjectSerializer> sınıfı.  
  
 [XmlSerializer Sınıfını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Neden ve nasıl açıklanmaktadır kullanmak için <xref:System.Xml.Serialization.XmlSerializer> sınıfı, bir alternatif <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.  
  
 [İleti Anlaşmaları Kullanma](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 İleti sözleşmeleri nasıl SOAP iletilerine ince denetime izin açıklar.  
  
 [İleti Sınıfını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 İleti sınıfı özelliklerinin nasıl kullanılacağını açıklar.  
  
 [Filtreleme](../../../../docs/framework/wcf/feature-details/filtering.md)  
 Filtreleme, açıklar çeşitli ölçütleri temel alarak bir ileti öncesi işlenmesini sağlar.  
  
 [Büyük Veriler ve Akış Yapma](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 Bir ikili dosya gibi büyük bir veri bloğunu göndermeyi açıklar.  
  
 [Veriler için Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 Veri aktarma ve seri hale getirme programlamada dikkat edilmesi gereken öğeleri açıklar.  
  
 [Veri Aktarımı Mimarisi Genel Bakış](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 WCF veri aktarımı genel tasarımını görünümünü açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kodlayıcılar ve Seri Hale Getiricileri Genişletme](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Hizmet Sürümü Oluşturma](../../../../docs/framework/wcf/service-versioning.md)
