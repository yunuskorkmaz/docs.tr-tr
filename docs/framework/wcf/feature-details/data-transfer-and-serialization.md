---
description: 'Hakkında daha fazla bilgi edinin: Veri Aktarımı ve serileştirme'
title: Veri Aktarma ve Seri Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 50e5068efc10d706fb9ce2634998408e48037ded
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756571"
---
# <a name="data-transfer-and-serialization"></a>Veri Aktarma ve Seri Hale Getirme

Bağlı bir sistemde, hizmetler ve istemciler herhangi bir görevi gerçekleştirmek için veri değişimine bağımlıdır. Bir hizmet veya istemcinin geliştiricisi olarak, verimli ve kolay uygulamalar oluşturmak için Windows Communication Foundation (WCF) veri ve veri serileştirmesini nasıl işlediğini de anlamanız gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Hizmet Sözleşmelerinde Veri Aktarımını Belirtme](specifying-data-transfer-in-service-contracts.md)  
 Hizmetler 'de veri aktarımının temel kavramlarını açıklar.  
  
 [Veri Sözleşmelerini Kullanma](using-data-contracts.md)  
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

- [En İyi Yöntemler: Veri Sözleşmesi Sürümü Oluşturma](../best-practices-data-contract-versioning.md)
- [Hizmet Sürümü Oluşturma](../service-versioning.md)
