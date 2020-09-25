---
title: DataSet içinde XML kullanma
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: e133da727887271af3bc5330a5779df4af58a37e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201193"
---
# <a name="using-xml-in-a-dataset"></a>DataSet içinde XML kullanma

ADO.NET ile bir <xref:System.Data.DataSet> XML akışından veya belgesinden bir örneği doldurabilirsiniz. XML akışını veya belgeyi, <xref:System.Data.DataSet> verileri, şema bilgilerini ya da her ikisini sağlamak için kullanabilirsiniz. XML akışından veya belgesinden sağlanan bilgiler, içinde zaten mevcut olan mevcut verilerle veya şema bilgileriyle birleştirilebilir <xref:System.Data.DataSet> .  
  
 Ayrıca, <xref:System.Data.DataSet> <xref:System.Data.DataSet> başka bir uygulama veya XML özellikli platform tarafından kullanılmak üzere http üzerinden taşımak için, şeması ile veya olmadan bir XML temsili oluşturmanıza da olanak sağlar. Bir öğesinin XML gösteriminde <xref:System.Data.DataSet> , VERILER XML biçiminde yazılır ve bu şema, temsilde satır içi IÇERIYORSA XML şeması tanım dili (xsd) kullanılarak yazılır. XML ve XML şeması, <xref:System.Data.DataSet> uzak istemcilerden ve içindeki içeriğini aktarmaya yönelik kolay bir biçim sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [DiffGrams](diffgrams.md)  
 Öğesinin içeriğini okumak ve yazmak için kullanılan bir XML biçimi olan DiffGram üzerinde ayrıntılar sağlar <xref:System.Data.DataSet> .  
  
 [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)  
 Bir XML belgesinden bir öğesinin içeriğini yüklerken göz önünde bulundurmanız gereken farklı seçenekleri açıklar <xref:System.Data.DataSet> .  
  
 [XML Verileri Olarak DataSet İçeriği Yazma](writing-dataset-contents-as-xml-data.md)  
 Bir <xref:System.Data.DataSet> as XML verisi içeriğini ve kullanabileceğiniz farklı XML biçimi seçeneklerini nasıl üretebileceğinizi açıklar.  
  
 [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)  
 <xref:System.Data.DataSet>XML 'nin şemasını yüklemek için kullanılan yöntemleri açıklar <xref:System.Data.DataSet> .  
  
 [XSD Olarak DataSet Schema Bilgilerini Yazma](writing-dataset-schema-information-as-xsd.md)  
 Bir XML şeması için kullanımları ve öğesinden bir oluşturma hakkında ele alınmaktadır <xref:System.Data.DataSet> .  
  
 [DataSet ve XmlDataDocument Eşitlemesi](dataset-and-xmldatadocument-synchronization.md)  
 Tek bir veri kümesinin hem ilişkisel hem de hiyerarşik görünümlerine zaman uyumlu erişim .NET Framework, ve arasında zaman uyumlu bir ilişki oluşturmayı gösteren özelliği ele alır <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> .  
  
 [DataRelations’ı İç İçe Yerleştirme](nesting-datarelations.md)  
 <xref:System.Data.DataRelation>XML verilerinin bir as içeriğini temsil eden iç içe nesnelerin önemini açıklar <xref:System.Data.DataSet> ve bunların nasıl oluşturulacağını açıklar.  
  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XML şemasından oluşturulan öğesinin ilişkisel yapısını veya şemasını açıklar <xref:System.Data.DataSet> .  
  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)  
 XML öğelerinden çıkarlandığınızda oluşturulan öğesinin elde edilen ilişkisel yapısını veya şemasını açıklar <xref:System.Data.DataSet> .  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [ADO.NET’e Genel Bakış](../ado-net-overview.md)  
 ADO.NET mimarisini ve bileşenlerini ve mevcut veri kaynaklarına erişmek için bunların yanı sıra uygulama verilerini yönetmek için nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
