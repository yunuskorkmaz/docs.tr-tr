---
title: DataSet içinde XML kullanma
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: ba68f0fbe84a9877596ddfefd56f71a5889cf8de
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203146"
---
# <a name="using-xml-in-a-dataset"></a>DataSet içinde XML kullanma
ADO.NET ile bir XML akışından veya <xref:System.Data.DataSet> belgesinden bir örneği doldurabilirsiniz. XML akışını veya belgeyi, verileri, şema bilgilerini ya da her <xref:System.Data.DataSet> ikisini sağlamak için kullanabilirsiniz. XML akışından veya belgesinden sağlanan bilgiler, <xref:System.Data.DataSet>içinde zaten mevcut olan mevcut verilerle veya şema bilgileriyle birleştirilebilir.  
  
 Ayrıca, başka bir uygulama veya XML özellikli platform tarafından kullanılmak <xref:System.Data.DataSet>üzere http <xref:System.Data.DataSet> üzerinden taşımak için, şeması ile veya olmadan bir XML temsili oluşturmanıza da olanak sağlar. Bir <xref:System.Data.DataSet>öğesinin xml gösteriminde, veriler XML biçiminde yazılır ve bu şema, temsilde satır içi içeriyorsa XML şeması tanım dili (xsd) kullanılarak yazılır. XML ve XML şeması, uzak istemcilerden ve içindeki içeriğini <xref:System.Data.DataSet> aktarmaya yönelik kolay bir biçim sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DiffGrams](diffgrams.md)  
 Öğesinin içeriğini okumak ve yazmak için kullanılan bir XML biçimi olan DiffGram üzerinde ayrıntılar sağlar <xref:System.Data.DataSet>.  
  
 [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)  
 Bir XML belgesinden bir <xref:System.Data.DataSet> öğesinin içeriğini yüklerken göz önünde bulundurmanız gereken farklı seçenekleri açıklar.  
  
 [XML Verileri Olarak DataSet İçeriği Yazma](writing-dataset-contents-as-xml-data.md)  
 Bir <xref:System.Data.DataSet> as XML verisi içeriğini ve kullanabileceğiniz farklı XML biçimi seçeneklerini nasıl üretebileceğinizi açıklar.  
  
 [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)  
 XML 'nin şemasını yüklemek için kullanılan yöntemleriaçıklar.<xref:System.Data.DataSet> <xref:System.Data.DataSet>  
  
 [XSD Olarak DataSet Schema Bilgilerini Yazma](writing-dataset-schema-information-as-xsd.md)  
 Bir XML şeması için kullanımları ve öğesinden <xref:System.Data.DataSet>bir oluşturma hakkında ele alınmaktadır.  
  
 [DataSet ve XmlDataDocument Eşitlemesi](dataset-and-xmldatadocument-synchronization.md)  
 Tek bir veri kümesinin hem ilişkisel hem de hiyerarşik görünümlerine zaman uyumlu erişim .NET Framework, ve arasında <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument>zaman uyumlu bir ilişki oluşturmayı gösteren özelliği ele alır.  
  
 [DataRelations’ı İç İçe Yerleştirme](nesting-datarelations.md)  
 XML verilerinin bir <xref:System.Data.DataSet> as içeriğini <xref:System.Data.DataRelation> temsil eden iç içe nesnelerin önemini açıklar ve bunların nasıl oluşturulacağını açıklar.  
  
 [XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XML şemasından oluşturulan öğesinin <xref:System.Data.DataSet> ilişkisel yapısını veya şemasını açıklar.  
  
 [XML’den DataSet İlişkisel Yapısını Çıkarma](inferring-dataset-relational-structure-from-xml.md)  
 XML öğelerinden çıkarlandığınızda oluşturulan öğesinin <xref:System.Data.DataSet> elde edilen ilişkisel yapısını veya şemasını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET’e Genel Bakış](../ado-net-overview.md)  
 ADO.NET mimarisini ve bileşenlerini ve mevcut veri kaynaklarına erişmek için bunların yanı sıra uygulama verilerini yönetmek için nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
