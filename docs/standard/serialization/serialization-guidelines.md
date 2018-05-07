---
title: Seri hale getirme yönergeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
ms.openlocfilehash: 51d561009a2f497cf4cf720abd5a414cbbbb2e64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="serialization-guidelines"></a>Seri hale getirme yönergeleri
Bu belgenin bir API tasarlama serileştirilecek göz önünde için yönergeleri listeler.  

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
 .NET çeşitli serileştirme senaryolar için iyileştirilen üç ana serileştirme teknolojiler sunar. Aşağıdaki tabloda bu teknolojiler ve teknolojiler için ilgili ana .NET türlerini listeler.  
  
|Teknoloji|İlgili sınıflar|Notlar|  
|----------------|----------------------|-----------|  
|Veri sözleşmesi seri hale getirme|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|Genel kalıcılığı<br /><br /> Web Hizmetleri<br /><br /> JSON|  
|XML seri hale getirme|<xref:System.Xml.Serialization.XmlSerializer>|XML biçimi <br />ile tam denetim|  
|Çalışma zamanı-seri hale getirme (ikili ve SOAP)|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET uzaktan iletişim|  
  
 Yeni türleri tasarımı yaparken, varsa, bu teknolojiler türlerden desteklemesi gerekir. karar. Bu seçim yapın ve bu tür desteğini sağlamak nasıl aşağıdaki yönergeleri açıklanmaktadır. Bu yönergeleri uygulamanızın veya kitaplık uygulamasında kullanması gereken hangi serileştirme teknolojiyi seçmenizde yardımcı anlamına gelmez. Bu tür yönergeleri için API tasarım doğrudan ilişkili değildir ve bu nedenle bu konu kapsamında değildir.  
  
## <a name="guidelines"></a>Kuralları  
  
-   Yeni türleri tasarım serileştirme hakkında düşünün.  
  
     Seri hale getirme herhangi bir türü için bir önemli tasarım husus çünkü programlar devam veya türdeki örneklerin aktarmak gerekebilir.  
  
### <a name="choosing-the-right-serialization-technology-to-support"></a>Sağ serileştirme teknolojisini desteklemek için seçme  
 Belirtilen her türlü none, bir veya daha fazla seri hale getirme teknolojilerini destekler.  
  
-   DÜŞÜNÜN destekleyen *veri sözleşmesi seri hale getirme* türünüz örneklerini kalıcı veya Web Hizmetleri içinde kullanılan gerekiyorsa.  
  
-   DÜŞÜNÜN destekleyen *XML serileştirme* yerine veya türü serileştirildiğinde üreten XML biçimi hakkında daha fazla denetime ihtiyacınız varsa veri sözleşmesi seri hale getirme yanı sıra.  
  
     Veri sözleşmesi seri hale getirme tarafından XML özniteliği üretmek için örneğin, desteklenmeyen bir XML Yapısı kullanmanıza gerek olduğu bazı birlikte çalışabilirlik senaryolarda gerekli olabilir.  
  
-   DÜŞÜNÜN destekleyen *çalışma zamanı serileştirme* türünüz örnekleri .NET uzaktan iletişim sınırlarında seyahat gerekiyorsa.  
  
-   Sadece genel Kalıcılık nedenlerle destekleme çalışma zamanı serileştirme veya XML serileştirme özen gösterin. Veri sözleşmesi seri hale getirme yerine tercih  
  
#### <a name="supporting-data-contract-serialization"></a>Destekleyici veri sözleşmesi seri hale getirme  
 Türlerini destekleyebilir veri sözleşmesi seri hale getirme uygulayarak <xref:System.Runtime.Serialization.DataContractAttribute> türüne ve <xref:System.Runtime.Serialization.DataMemberAttribute> türü üyeleri (alanları ve özellikleri).  
  
 [!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)]
 [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]  
  
1.  Veri üyeleri türünüze türü kısmi güvende kullanılıp kullanılamayacağını ortak olarak işaretlemeyi DÜŞÜNÜN. Tam güven veri sözleşmesi serileştiricileri seri hale getirmek ve seri durumdan ortak olmayan türleri ve üyeleri, ancak yalnızca Genel üyeler sıralanabilir ve kısmi güvende serisi.  
  
2.  Alıcı hem de ayarlayıcı veri MemberAttribute sahip tüm özellikleri uygulayın. Veri sözleşmesi serileştiricileri hem alıcı hem de ayarlayıcı türü seri hale getirilebilir kabul edilmesi gerektirir. Kısmi güvende türü kullanılmaz, bir veya iki özellik erişimcisi ortak olmayan olabilir.  
  
     [!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]
     [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]  
  
3.  Seri durumdan çıkarılmış örnekleri başlatma için serileştirme geri çağırmaları kullanmayı DÜŞÜNÜN.  
  
     Nesneleri seri olduğunda oluşturucular çağrılır değil. Bu nedenle, normal oluşturma sırasında yürütür herhangi bir mantık biri olarak uygulanması gereken *seri hale getirme geri çağrıları*.  
  
     [!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]
     [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]  
  
     <xref:System.Runtime.Serialization.OnDeserializedAttribute> En yaygın kullanılan geri çağırma özniteliği bir özniteliktir. Ailesindeki diğer öznitelikleri <xref:System.Runtime.Serialization.OnDeserializingAttribute>,    
    <xref:System.Runtime.Serialization.OnSerializingAttribute>, ve <xref:System.Runtime.Serialization.OnSerializedAttribute>. Seri durumundan çıkarma, serileştirme önce ve son olarak seri hale getirme sonra önce sırasıyla yürütülen geri çağırmaları işaretlemek için kullanılabilir.  
  
4.  DÜŞÜNÜN kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute> karmaşık Nesne grafiği işlenirken kullanılması gereken somut türler belirtmek için.  
  
     Örneğin, bir seri durumdan çıkarılmış veri üyesi türü soyut bir sınıf tarafından temsil edilen, seri hale getirici gerekir *türü bilinen* örneği ve üyesine atamak için somut türüne karar vermek için bilgi. Bilinen türü özniteliği kullanılarak belirtilmezse için seri hale getirici açıkça geçirilmesi gerekir (bunu bilinen türler seri hale getirici oluşturucusuna geçirerek yapabilirsiniz) veya yapılandırma dosyasında belirtilmesi gerekir.  
  
     [!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]
     [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]  
  
     Burada bilinen türleri listesini değil bilinen statik olarak durumlarda (zaman **kişi** sınıfı derlenmiş), **KnownTypeAttribute** çalışma zamanında bilinen türlerinin bir listesini döndüren bir yöntem de işaret edebilir.  
  
5.  Oluştururken veya serializable türler değiştirme İleri ve geriye dönük uyumluluk düşünün.  
  
     Türünüz gelecek sürümlerinde akışları serileştirilmiş unutmayın türü geçerli sürüme serisi ve bunun tam tersi. Veri sözleşmesi öznitelikleri için açık parametrelerini kullanarak sözleşme korumak için özellikle dikkatli geçen sürece veri üyeleri, özel ve iç, bile adlarını, türlerini veya bile sıralarına türü gelecekteki sürümlerinde değiştiremezsiniz anladığınızdan emin olun . Seri hale getirme uyumluluğu için seri hale getirilebilir türler değişiklik yaparken sınayın. Yeni sürümü eski bir sürümüne seri durumdan deneyin ve tersi.  
  
6.  DÜŞÜNÜN uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> türü farklı sürümleri arasında gidiş izin vermek için arabirim.  
  
     Arabirim gidiş sırasında veri kaybı olmamasına emin olmak seri hale getirici sağlar. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> Özelliği olan geçerli sürümü için bilinmeyen tür, gelecekteki sürümüne tüm verileri depolar. Geçerli sürüm sonradan serileştirilen ve gelecekteki bir sürümüne seri, ek verileri serileştirilmiş akış içindeki kullanılabilir **ExtensionData** özellik değeri.  
  
     [!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]
     [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]  
  
     Daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
#### <a name="supporting-xml-serialization"></a>XML serileştirme destekleme  
 Veri sözleşmesi seri hale getirme (varsayılan) ana olan .NET Framework serileştirme teknolojisinde ancak vardır veri seri hale getirme sözleşmesi seri hale getirme senaryoları desteklemez. Örneğin, bunu, üretilen veya seri hale getirici tarafından tüketilen XML şekli üzerinde tam denetim sağlamaz. Bu tür daha iyi denetim gerekiyorsa *XML serileştirme* kullanılmak üzere vardır ve bu serileştirme teknolojisini desteklemek için türlerinizi tasarlamanız gerekir.  
  
1.  Üretilen XML şeklini denetlemek için çok güçlü bir nedeniniz yoksa, türlerinizi XML serileştirmesi için özellikle tasarlama KAÇININ. Veri sözleşmesi önceki bölümde açıklanan seri hale getirme bu serileştirme teknoloji almıştır.  
  
     Diğer bir deyişle, öznitelikleri uygulama <xref:System.Runtime.Serialization> yeni türleri için ad alanı türü XML serileştirilmesi ile kullanılacak bilmiyorsanız. Aşağıdaki örnekte gösterildiği nasıl **dizileştirme mekanizmasını System.Xml.Serialization** XML şeklini denetlemek için kullanılan-üretilen.  
  
     [!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]
     [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]  
  
2.  DÜŞÜNÜN uygulama <xref:System.Xml.Serialization.IXmlSerializable> ne XML serileştirme özniteliklerini uygulayarak sunulan daha serileştirilmiş XML şekli üzerinde daha fazla denetim isterseniz, arabirim. İki yöntem arabiriminin <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> ve <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, tam olarak serileştirilmiş XML akışı denetlemenize olanak sağlar. Türü için uygulanarak oluşturulan XML Şeması kontrol edebilirsiniz <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği.  
  
#### <a name="supporting-runtime-serialization"></a>Çalışma zamanı serileştirme destekleme  
 *Çalışma zamanı serileştirme* .NET uzaktan iletişim tarafından kullanılan bir teknolojisidir. .NET uzaktan iletişim kullanarak türlerinizi taşınır düşünüyorsanız, çalışma zamanı serileştirme desteklediğinden emin olmanız gerekir.  
  
 İçin temel destek *çalışma zamanı serileştirme* uygulama tarafından sağlanan <xref:System.SerializableAttribute> özniteliği ve daha Gelişmiş senaryolar içeren basit bir uygulama *çalışma zamanı seri hale getirilebilir düzeni* () Uygulama -<xref:System.Runtime.Serialization.ISerializable> ve seri hale getirme Oluşturucusu sağlar).  
  
1.  Çalışma zamanı serileştirme türlerinizi .NET uzaktan iletişim ile kullanılacaksa destekleyen DÜŞÜNÜN. Örneğin, <xref:System.AddIn> ad alanı .NET uzaktan iletişim kullanır ve böylece tüm türleri akar arasında **System.AddIn** eklentileri gereken çalışma zamanı serileştirme desteklemek.  
  
     [!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]
     [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]  
  
2.  DÜŞÜNÜN uygulama *çalışma zamanı seri hale getirilebilir düzeni* seri hale getirme işlemi üzerinde tam denetim istiyorsanız. Örneğin, verileri olarak dönüştürmek istiyorsanız seri durumdan veya serileştirilir.  
  
     Düzen çok basit yöneliktir. Yapmanız gereken tek şey uygulamak <xref:System.Runtime.Serialization.ISerializable> arabirim ve nesnenin seri durumda olduğunda kullanılan özel bir oluşturucu sağlayın.  
  
     [!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]
     [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]  
  
3.  Korumalı serileştirme Oluşturucusu yapın ve yazılan ve tam olarak burada aşağıdaki örnekte gösterildiği gibi adlı iki parametre sağlayın.  
  
     [!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]
     [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]  
  
4.  ISerializable üyelerini açıkça uygulayın.  
  
     [!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]
     [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]  
  
5.  Bir bağlantı isteği uygulamak **ISerializable.GetObjectData** uygulaması. Bu, yalnızca tam olarak çekirdek ve çalışma zamanı seri hale getirici üye erişimi güvenilir sağlar.  
  
     [!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]
     [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Veri Anlaşmalarını Kullanma](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Veri Anlaşması Seri Hale Getirici](../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 [Veri Anlaşması Seri Hale Getirici Tarafından Desteklenen Türler](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)  
 [İkili Serileştirme](binary-serialization.md)  
 [Uzak nesneleri](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)  
 [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)  
 [Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)
