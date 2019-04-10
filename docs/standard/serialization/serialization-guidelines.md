---
title: Serileştirme yönergeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
ms.openlocfilehash: 05cbe8b18a0d9635091b373d0acddb2ba665cc37
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317343"
---
# <a name="serialization-guidelines"></a>Serileştirme yönergeleri
Bu belgenin bir API tasarlama serileştirilecek göz önünde için yönergeleri listeler.  

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
 .NET, çeşitli serileştirme senaryolar için optimize edilmiş üç ana serileştirme teknolojiler sunar. Aşağıdaki tabloda bu teknolojiler ve bu teknolojiler için ilgili ana .NET türleri listelenmektedir.  
  
|Teknoloji|İlgili sınıflar|Notlar|  
|----------------|----------------------|-----------|  
|Veri sözleşme seri hale getirme|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|Genel kalıcılığı<br /><br /> Web Hizmetleri<br /><br /> JSON|  
|XML seri hale getirme|<xref:System.Xml.Serialization.XmlSerializer>|XML biçimi <br />ile tam denetim|  
|Çalışma zamanı-seri hale getirme (ikili ve SOAP)|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET uzaktan iletişim|  
  
 Yeni türleri tasarımı yaparken, varsa, bu teknolojiler türlerden desteklemesi gerekir. karar. Bu seçim yapın ve bu tür desteğini sağlamak nasıl aşağıdaki yönergeleri açıklanmaktadır. Bu yönergeleri uygulamanızın veya kitaplık uygulamasında kullanması gereken hangi serileştirme teknolojiyi seçmenizde yardımcı anlamına gelmez. Bu tür yönergeleri için API tasarım doğrudan ilişkili değildir ve bu nedenle bu konu kapsamında değildir.  
  
## <a name="guidelines"></a>Kuralları  
  
-   Yeni türleri tasarım serileştirme hakkında düşünün.  
  
     Serileştirme herhangi bir tür için bir önemli tasarım husus çünkü programlar sürdürülmesi veya aktarım türü örneklerini gerekebilir.  
  
### <a name="choosing-the-right-serialization-technology-to-support"></a>Destek için sağ serileştirme teknolojiyi seçmenizde  
 Belirtilen her türlü none, bir veya daha fazla seri hale getirme teknolojilerini destekler.  
  
-   DÜŞÜNÜN destekleyen *veri sözleşme serileştirme* örneklerinin kalıcı veya kullanılan Web Hizmetleri gerekiyorsa.  
  
-   DÜŞÜNÜN destekleyen *XML serileştirme* yerine veya türü seri olduğunda, üretilen XML biçimi hakkında daha fazla denetime ihtiyacınız varsa, veri sözleşme serileştirme yanı sıra.  
  
     Bu, veri sözleşme seri hale getirme tarafından Örneğin, XML özniteliği üretmek için desteklenmeyen bir XML yapı kullanmak için gereken yere bazı birlikte çalışabilirlik senaryolarında gerekli olabilir.  
  
-   DÜŞÜNÜN destekleyen *çalışma zamanı serileştirme* örneklerinin .NET uzaktan iletişim sınırlarında yolculuk gerekiyorsa.  
  
-   Sadece genel Kalıcılık nedenlerle destekleme çalışma zamanı serileştirme veya XML serileştirme özen gösterin. Bunun yerine veri sözleşme serileştirme tercih  
  
#### <a name="supporting-data-contract-serialization"></a>Destek veri sözleşme seri hale getirme  
 Türleri uygulayarak veri sözleşme serileştirme destekleyebilir <xref:System.Runtime.Serialization.DataContractAttribute> türüne ve <xref:System.Runtime.Serialization.DataMemberAttribute> üyelerine (alanlar ve Özellikler) türü.  
  
 [!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)]
 [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]  
  
1. Veri üyeleri türünüz ortak türü kısmi güvende kullanılabilir işaretlemeyi DÜŞÜNÜN. Tam güven veri sözleşme serileştiricileri seri hale getirmek ve özel tür ve üyelerinin seri durumdan, ancak yalnızca ortak üyeleri sıralanabilir ve kısmi güvende seri durumdan.  
  
2. Alıcı ve Ayarlayıcıyı veri MemberAttribute sahip tüm özellikleri uygular. Veri sözleşme serileştiricileri alıcı hem seri hale getirilebilir değerlendirilmesi türünün ayarlama gerektirir. Kısmi güven türü kullanılmaz, bir veya iki özellik erişimcisi özel olabilir.  
  
     [!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]
     [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]  
  
3. Seri durumdan çıkarılmış örnekleri başlatma için serileştirme geri çağırmaları kullanmayı DÜŞÜNÜN.  
  
     Nesneleri seri zaman oluşturucular çağrılır değil. Bu nedenle, normal yapım sırasında yürüten mantığı herhangi biri olarak uygulanması gereken *serileştirme geri çağırmaları*.  
  
     [!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]
     [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]  
  
     <xref:System.Runtime.Serialization.OnDeserializedAttribute> En yaygın kullanılan geri çağırma özniteliği bir özniteliktir. Diğer öznitelikler ailesindeki <xref:System.Runtime.Serialization.OnDeserializingAttribute>,    
    <xref:System.Runtime.Serialization.OnSerializingAttribute>, ve <xref:System.Runtime.Serialization.OnSerializedAttribute>. Seri durumundan çıkarma, serileştirme önce ve son olarak seri hale getirme sonra önce sırasıyla yürütülen geri çağırmaları işaretlemek için kullanılabilir.  
  
4. DÜŞÜNÜN kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute> karmaşık Nesne grafiği işlenirken kullanılması gereken somut türler belirtmek için.  
  
     Örneğin, bir türü seri durumdan çıkarılmış veri üyesi soyut bir sınıf tarafından temsil edilen seri hale getirici gerekir *türü bilinen* örneği oluşturmak ve üyesine atamak için hangi somut bir türde karar vermek için bilgi. Bilinen türü özniteliğini kullanarak belirtilmemişse, açıkça için seri hale getirici iletilecek gerekir (seri hale getirici oluşturucuya bilinen türleri ileterek bunu yapabilirsiniz) veya yapılandırma dosyasında belirtilmesi gerekir.  
  
     [!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]
     [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]  
  
     Burada bilinen türleri listesi değil bilinen statik olarak durumlarda (olduğunda **kişi** sınıfı derlenmiş), **KnownTypeAttribute** zamanında bilinen türlerinin bir listesini döndüren bir yöntem da işaret edebilir.  
  
5. Oluştururken veya serializable türler değiştirme İleri ve geriye dönük uyumluluk düşünün.  
  
     Akış türünüz sonraki sürümlerinde serileştirilmiş unutmayın türü geçerli sürüme seri ve tersi. Özel veri sözleşme öznitelikleri için açık parametrelerini kullanarak sözleşme korumak için açıklanmamasına sürece veri üyeleri, hatta özel ve dahili, adları, türleri veya hatta sıralamalarını türü gelecekteki sürümlerinde değiştiremezsiniz anlamak emin olun . Serileştirme uyumluluk serializable türler için değişiklik yaparken test edin. Yeni sürümü eski bir sürüme serisi kaldırılırken deneyin ve tersi.  
  
6. DÜŞÜNÜN uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> türü farklı sürümleri arasında gidiş dönüşü izin vermek için arabirim.  
  
     Seri hale getirici gidiş dönüşü sırasında hiçbir veri kaybı olduğundan emin olmak arabirim sağlar. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> Özelliği olan geçerli sürümü için bilinmeyen tür, gelecekteki sürümüne tüm verileri depolar. Geçerli sürüm daha sonra serileştirilmiş ve gelecekteki bir sürümüne seri durumdan, ek verileri seri hale getirilmiş akış kullanılabilir **ExtensionData** özellik değeri.  
  
     [!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]
     [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]  
  
     Daha fazla bilgi için [İleri uyumlu veri sözleşmeleri](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
#### <a name="supporting-xml-serialization"></a>XML serileştirme destekleme  
 Veri sözleşme seri hale getirme (varsayılan) ana olan serileştirme teknoloji .NET Framework, ancak vardır verileri seri hale getirme sözleşme serileştirme senaryoları desteklemiyor. Örneğin, bu, üretilen veya serileştiricisi tarafından kullanılan XML şekli üzerinde tam denetim vermez. Bu tür iyi denetim gerekliyse *XML serileştirme* kullanılması gerekir ve bu serileştirme teknoloji desteklemek için türleri tasarlamak için ihtiyacınız.  
  
1. Üretilen XML şeklini denetlemek için çok güçlü bir neden olmadıkça, türlerinizi XML serileştirme için özel olarak tasarlama özen gösterin. Bu seri hale getirme teknoloji önceki bölümde açıklanan veri sözleşme serileştirme yerini almıştır.  
  
     Diğer bir deyişle, öznitelikleri uygulama <xref:System.Xml.Serialization> yeni türleri için ad alanı türü ile XML serileştirme kullanılacak bilmiyorsanız. Aşağıdaki örnekte gösterildiği nasıl **System.Xml.Serialization** XML şeklini denetlemek için kullanılan-üretilen.  
  
     [!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]
     [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]  
  
2. DÜŞÜNÜN uygulama <xref:System.Xml.Serialization.IXmlSerializable> ne XML serileştirme öznitelikleri uygulayarak sunulan değerinden daha fazla denetime serileştirilmiş XML şeklini istiyorsanız, arabirim. İki yöntem arabirimin <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> ve <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, tam olarak serileştirilmiş XML akışı denetlemek izin. Türü için uygulama tarafından oluşturulan XML Şeması de denetleyebilirsiniz <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliği.  
  
#### <a name="supporting-runtime-serialization"></a>Çalışma zamanı serileştirme destekleme  
 *Çalışma zamanı serileştirme* .NET uzaktan iletişim tarafından kullanılan bir teknolojisidir. .NET uzaktan iletişim kullanarak türlerinizi taşınır düşünüyorsanız, çalışma zamanı serileştirme destekledikleri emin olmanız gerekir.  
  
 Temel destek için *çalışma zamanı serileştirme* uygulama tarafından sağlanan <xref:System.SerializableAttribute> özniteliği ve daha gelişmiş senaryoları içeren basit bir uygulama *çalışma zamanı seri hale getirilebilir deseni* () Uygulama -<xref:System.Runtime.Serialization.ISerializable> ve bir seri hale getirme Oluşturucu sağlayın).  
  
1. Çalışma zamanı serileştirme türlerinizi .NET uzaktan iletişim ile kullanılacaksa destekleyen DÜŞÜNÜN. Örneğin, <xref:System.AddIn> ad alanı .NET uzaktan iletişim kullanır ve tüm türleri değiştirilen arasında **System.AddIn** add-INS çalışma zamanı serileştirme desteklemesi gerekir.  
  
     [!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]
     [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]  
  
2. DÜŞÜNÜN uygulama *çalışma zamanı seri hale getirilebilir deseni* seri hale getirme işlemi üzerinde tam denetim istiyorsanız. Verileri olarak dönüştürmek istiyorsanız, örneğin, dosya serileştirilmiş seri durumdan veya.  
  
     Düzen çok basit yöneliktir. Tek yapmak için ihtiyacınız olan uygulayan <xref:System.Runtime.Serialization.ISerializable> arabirim ve nesnenin seri durumda olduğunda kullanılan özel bir oluşturucu sağlayın.  
  
     [!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]
     [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]  
  
3. Korumalı serileştirme Oluşturucu olun ve yazılı ve burada örnekte gösterildiği gibi tam olarak adlı iki parametre sağlar.  
  
     [!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]
     [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]  
  
4. ISerializable üyelerini açıkça uygulayın.  
  
     [!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]
     [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]  
  
5. Bir bağlantı isteği için geçerli **ISerializable.GetObjectData** uygulaması. Bu, yalnızca tam olarak çekirdek ve çalışma zamanı seri hale getirici üye erişimi güvenilir sağlar.  
  
     [!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]
     [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Sözleşmelerini Kullanma](../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Veri Sözleşmesi Seri Hale Getirici](../../../docs/framework/wcf/feature-details/data-contract-serializer.md)
- [Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [İkili Serileştirme](binary-serialization.md)
- [.NET uzaktan iletişim](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))
- [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)
- [Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)
