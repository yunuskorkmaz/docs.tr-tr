---
title: Veri Sözleşmelerinde Numaralandırma Türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: 21f1f948e0bcd088cbe14316760708e10285124b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649316"
---
# <a name="enumeration-types-in-data-contracts"></a>Veri Sözleşmelerinde Numaralandırma Türleri
Numaralandırmalar veri sözleşme modelindeki ifade edilebilir. Bu konuda bir programlama modeli açıklayan birkaç örneklerle size yol gösterir.  
  
## <a name="enumeration-basics"></a>Numaralandırma temel bilgileri  
 Numaralandırma türleri veri sözleşme modelindeki kullanmanın tek yolu olduğundan uygulamak için <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik türü için. Ardından uygulamalısınız <xref:System.Runtime.Serialization.EnumMemberAttribute> öznitelik her üyesine veri sözleşmede eklenmelidir.  
  
 Aşağıdaki örnek, iki sınıf gösterir. İlk sabit kullanır ve ikinci sabit listesi tanımlar.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Örneği `Car` sınıfı gönderilen ya da yalnızca alınan `condition` alan değerlerden birine ayarlanır `New`, `Used`, veya `Rental`. Varsa `condition` olduğu `Broken` veya `Stolen`, <xref:System.Runtime.Serialization.SerializationException> oluşturulur.  
  
 Kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute> özellikleri (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ve <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) sabit listesi veri anlaşmaları için her zaman olduğu gibi.  
  
### <a name="enumeration-member-values"></a>Sabit listesi üyesi değerler  
 Genellikle veri anlaşması sabit listesi üye adları, sayısal değerler içerir. Ancak, bir WCF istemcisi alan tarafta ise, veri sözleşme modeli kullanırken, dışarı aktarılan şema sayısal değerleri korur. Bu durum kullanırken olmadığını unutmayın [XmlSerializer sınıfını kullanarak](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
 Önceki örnekte, `condition` ayarlanır `Used` ve verileri seri hale getirilmiş elde edilen XML XML için olan `<condition>Used</condition>` değil `<condition>1</condition>`. Bu nedenle, aşağıdaki veri anlaşması veri sözleşmesine eşdeğerdir `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Örneğin, kullanabileceğiniz `CarConditionEnum` Gönderen tarafında ve `CarConditionWithNumbers` alıcı tarafında. Gönderen tarafı için "1" değeri kullansa `Used` ve alma tarafı kullandığı değer "20" XML gösterimi `<condition>Used</condition>` iki tarafı için.  
  
 Veri sözleşmesi içerisinde bulunan için uygulamanız gereken <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], aynı zamanda tüm sabit listesi için varsayılan değer olan bir sabit listesi özel değeri 0 (sıfır) her zaman uygulayabilirsiniz. Ancak, bu özel sıfır değeri ile işaretlenmediği sürece serileştirilemiyor bile <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği.  
  
 Bu iki istisna mevcuttur:  
  
-   Bayrak sabit listeleri (Bu konunun ilerleyen bölümlerinde açıklanmıştır).  
  
-   Sabit listesi veri üyeleriyle <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliğini `false` (Bu durumda, sıfır değeri ile numaralandırma atlanırsa seri hale getirilmiş verilerden).  
  
### <a name="customizing-enumeration-member-values"></a>Sabit listesi üye değerlerinin özelleştirme  
 Veri anlaşması bir kısmını kullanarak form numaralandırma üyesi değeri özelleştirebilirsiniz <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> özelliği <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği.  
  
 Örneğin, aşağıdaki veri sözleşme ayrıca veri sözleşmesine eşdeğerdir `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Serileştirilmiş olduğunda, değerini `PreviouslyOwned` XML gösterimine sahip `<condition>Used</condition>`.  
  
## <a name="simple-enumerations"></a>Basit sabit listeleri  
 Numaralandırma türleri, aynı zamanda serileştirebiliyorsa <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği değil uygulandı. Bu tür sabit listesi türleri tam olarak işlendiği daha önce açıklandığı gibi hariç her üyesi (olmayan <xref:System.NonSerializedAttribute> özniteliği uygulandı) değerlendirilir gibi <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği uygulandı. Örneğin, aşağıdaki sabit listesi önceki eşdeğer bir veri anlaşması örtük olarak sahip `CarConditionEnum` örnek.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Sabit listesinin veri anlaşması adına ve ad alanı ve sabit listesi üye değerlerinin özelleştirmek gerekli olmadığında, basit sabit listeleri kullanabilirsiniz.  
  
#### <a name="notes-on-simple-enumerations"></a>Basit numaralandırmalar ile ilgili notlar  
 Uygulama <xref:System.Runtime.Serialization.EnumMemberAttribute> basit numaralandırmalar özniteliğine etkisizdir.  
  
 Olup olmadığını nasıl yönelttiğiniz fark etmez <xref:System.SerializableAttribute> özniteliği sabit listesine uygulanır.  
  
 Olgu, <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı sekme <xref:System.NonSerializedAttribute> numaralandırma üyelerini uygulanan öznitelik davranışından farklıdır <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Bu seri hale getiricileri genişletme her ikisi de Yoksay <xref:System.NonSerializedAttribute> özniteliği.  
  
## <a name="flag-enumerations"></a>Bayrak sabit listeleri  
 Uygulayabileceğiniz <xref:System.FlagsAttribute> sabit listeleri için özniteliği. Bu durumda, sıfır veya daha fazla numaralandırma değerlerinin listesini gönderilebilecek veya aynı anda aldı.  
  
 Bunu yapmak için uygulama <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bayrak sabit listesine ve ardından iki tabanların yer alan tüm üyelerin işaretleyin <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği. Bayrak sabit kullanmak için ilerlemeyi powers 2 (örneğin, 1, 2, 4, 8, 16, 32, 64), kesintisiz bir dizi olması gerektiğini unutmayın.  
  
 Bir bayrağın numaralandırma değeri göndermek için aşağıdaki adımları uygulayın:  
  
1.  Bir numaralandırma üyesine bulmaya (ile <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği uygulandı) sayısal değere eşler. Varsa bulunan, söz konusu üyeyi içeren bir liste Gönder.  
  
2.  Vardır numaralandırma üyelerini, sayısal değerin toplam kaldırmaya çalışan (her biri <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği uygulandı) her bir parçasının toplamı eşleyin. Bu üye listesini gönderin. Unutmayın *doyumsuz algoritması* böyle bir toplam bulmak için kullanılır ve bu nedenle, mevcut olsa bile, tür toplam bulunan bir garanti yoktur. Bu sorunu önlemek için sayısal değerlerin numaralandırma üyelerinin powers iki olduğundan emin olun.  
  
3.  Önceki iki adımı başarısız ve sayısal değer sıfır olmayan, throw bir <xref:System.Runtime.Serialization.SerializationException>. Sayısal değer sıfır ise, boş liste gönderin.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte sabit listesi bayrağı işleminde kullanılabilir.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Aşağıdaki örnek değerleri belirtildiği şekilde serileştirilir.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
