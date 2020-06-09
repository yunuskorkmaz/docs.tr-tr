---
title: Veri Aktarma ve Seri Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: b07937b0a94c24a934b17d6cf21b726ee0d4362e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593496"
---
# <a name="data-transfer-and-serialization"></a>Veri Aktarma ve Seri Hale Getirme
Bağlı bir sistemde, hizmetler ve istemciler herhangi bir görevi gerçekleştirmek için veri değişimine bağımlıdır. Bir hizmet veya istemcinin geliştiricisi olarak, verimli ve kolay uygulamalar oluşturmak için Windows Communication Foundation (WCF) veri ve veri serileştirmesini nasıl işlediğini de anlamanız gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](specifying-data-transfer-in-service-contracts.md)  
 Hizmetler 'de veri aktarımının temel kavramlarını açıklar.  
  
 [Veri Anlaşmalarını Kullanma](using-data-contracts.md)  
 Veri sözleşmelerinin ne olduğunu ve nasıl oluşturulacağını ve kullanılacağını açıklar.  
  
 [Veri Sözleşmesi Seri Hale Getirici](data-contract-serializer.md)  
 Sınıf veya sınıfın Uzantısı ile veri serileştirmesinin nasıl yapılacağını açıklar <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.XmlObjectSerializer> .  
  
 [XmlSerializer Sınıfını Kullanma](using-the-xmlserializer-class.md)  
 Sınıfının <xref:System.Xml.Serialization.XmlSerializer> bir alternatifi olan sınıfının nasıl ve nasıl kullanılacağını açıklar <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 [İleti Sözleşmeleri Kullanılıyor](using-message-contracts.md)  
 İleti sözleşmelerinin SOAP iletileri üzerinde ince denetime nasıl izin sağladığını açıklar.  
  
 [İleti Sınıfını Kullanma](using-the-message-class.md)  
 Ileti sınıfı özelliklerinin nasıl kullanılacağını açıklar.  
  
 [Filtreleme](filtering.md)  
 Farklı ölçütlere göre bir iletinin ön işlemesini sağlayan filtrelemeyi açıklar.  
  
 [Büyük Veriler ve Akış Yapma](large-data-and-streaming.md)  
 İkili dosya gibi büyük bir veri bloğunun nasıl gönderileceğini açıklar.  
  
 [Veriler için Güvenlik Konuları](security-considerations-for-data.md)  
 Veri aktarımı ve Serileştirmeyi programlarken haberdar edilecek öğeleri açıklar.  
  
 [Veri Aktarımı Mimarisi Genel Bakış](data-transfer-architectural-overview.md)  
 WCF 'de veri aktarımının genel tasarımının görünümünü açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kodlayıcılar ve Seri Hale Getiricileri Genişletme](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma](../best-practices-data-contract-versioning.md)
- [Hizmet Sürümü Oluşturma](../service-versioning.md)
