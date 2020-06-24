---
title: Veri Sözleşmelerinde Numaralandırma Türleri
description: Veri anlaşması modelinin Numaralandırmaların, WFC programlama modelinin bir parçası olarak nasıl ifade olduğunu öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: ff3184a285e88d47d4545a38a6c74b2f209827fb
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247305"
---
# <a name="enumeration-types-in-data-contracts"></a>Veri Sözleşmelerinde Numaralandırma Türleri
Numaralandırmalar veri sözleşmesi modelinde ifade edilebilir. Bu konuda, programlama modelini açıklayan birkaç örnek gösterilmektedir.  
  
## <a name="enumeration-basics"></a>Sabit Listesi temelleri  
 Veri anlaşması modelinde numaralandırma türlerini kullanmanın bir yolu, <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğini türüne uygulamaktır. Daha sonra, <xref:System.Runtime.Serialization.EnumMemberAttribute> veri sözleşmesine dahil olması gereken her üyeye özniteliğini uygulamanız gerekir.  
  
 Aşağıdaki örnekte iki sınıf gösterilmektedir. İlki numaralandırmayı kullanır ve ikincisi numaralandırmayı tanımlar.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Sınıfının bir örneği `Car` yalnızca `condition` alan, veya değerlerinden birine ayarlanmışsa gönderilebilir veya alınabilir `New` `Used` `Rental` . `condition`Veya ise, `Broken` `Stolen` bir oluşturulur <xref:System.Runtime.Serialization.SerializationException> .  
  
 <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> Sıralama verileri sözleşmeleri için her zamanki gibi özellikleri (ve) kullanabilirsiniz.  
  
### <a name="enumeration-member-values"></a>Sabit listesi üyesi değerleri  
 Genellikle veri sözleşmesi sayısal değerleri değil sabit listesi üye adlarını içerir. Ancak, veri anlaşması modelini kullanırken, alıcı tarafı bir WCF istemcesede, bu şema sayısal değerleri korur. Bu, [XmlSerializer sınıfı kullanılarak](using-the-xmlserializer-class.md)kullanılırken bu durum değildir.  
  
 Önceki örnekte, `condition` olarak ayarlanmışsa `Used` ve veriler XML olarak serileştirilildiğinde, sonuçta elde edilen XML `<condition>Used</condition>` değildir `<condition>1</condition>` . Bu nedenle, aşağıdaki veri sözleşmesi veri sözleşmesiyle eşdeğerdir `CarConditionEnum` .  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Örneğin, `CarConditionEnum` gönderme ve alma tarafında ' ı kullanabilirsiniz `CarConditionWithNumbers` . Gönderme tarafı için "1" değerini, ancak `Used` alan tarafı "20" değerini kullanıyorsa, XML temsili `<condition>Used</condition>` her iki taraf için de kullanılır.  
  
 Veri sözleşmesine eklenmek için özniteliği uygulamanız gerekir <xref:System.Runtime.Serialization.EnumMemberAttribute> . .NET Framework, her zaman bir numaralandırma için varsayılan değer olan 0 (sıfır) özel değerini bir numaralandırmaya uygulayabilirsiniz. Ancak, bu özel sıfır değeri, özniteliğiyle işaretlenmedikçe seri hale getirilemez <xref:System.Runtime.Serialization.EnumMemberAttribute> .  
  
 Bunun için iki özel durum vardır:  
  
- Bayrak numaralandırmalar (Bu konunun ilerleyen kısımlarında açıklanmıştır).  
  
- Özelliği olarak ayarlanmış sabit listesi veri üyeleri <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> `false` (Bu durumda, sıfır değerine sahip sabit listesi serileştirilmiş verilerden çıkarılır).  
  
### <a name="customizing-enumeration-member-values"></a>Numaralandırma üyesi değerlerini özelleştirme  
 Özniteliğin özelliğini kullanarak veri sözleşmesinin bir parçasını oluşturan sabit listesi üye değerini özelleştirebilirsiniz <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> <xref:System.Runtime.Serialization.EnumMemberAttribute> .  
  
 Örneğin, aşağıdaki veri sözleşmesi, veri sözleşmesine de eşdeğerdir `CarConditionEnum` .  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Serileştirilmiş olduğunda, değerinin `PreviouslyOwned` XML temsili vardır `<condition>Used</condition>` .  
  
## <a name="simple-enumerations"></a>Basit numaralandırmalar  
 Ayrıca özniteliğin uygulanmadığı numaralandırma türlerini seri hale getirebilirsiniz <xref:System.Runtime.Serialization.DataContractAttribute> . Bu tür numaralandırma türleri, her üyenin ( <xref:System.NonSerializedAttribute> özniteliği uygulanmamış), öznitelik uygulanmış gibi değerlendirildiğinden, tam olarak açıklandığı gibi değerlendirilir <xref:System.Runtime.Serialization.EnumMemberAttribute> . Örneğin, aşağıdaki numaralandırmada, önceki örneğe denk olarak bir veri anlaşması vardır `CarConditionEnum` .  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Numaralandırmanın veri sözleşmesi adını ve ad alanını ve numaralandırma üyesi değerlerini özelleştirmeniz gerekmiyorsa basit numaralandırmalar kullanabilirsiniz.  
  
#### <a name="notes-on-simple-enumerations"></a>Basit Numaralandırmalar hakkında notlar  
 <xref:System.Runtime.Serialization.EnumMemberAttribute>Özniteliği basit numaralandırmalara uygulamak hiçbir etkiye sahip değildir.  
  
 <xref:System.SerializableAttribute>Özniteliğin numaralandırmaya uygulanıp uygulanmadığı fark etmez.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>Sınıfın, <xref:System.NonSerializedAttribute> numaralandırma üyelerine uygulanan özniteliği, ve ' nin davranışından farklı olduğunu unutmayın <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . Bu serileştiricilerin her ikisi de <xref:System.NonSerializedAttribute> özniteliğini yoksayar.  
  
## <a name="flag-enumerations"></a>Bayrak numaralandırmalar  
 <xref:System.FlagsAttribute>Özniteliği numaralandırmalara uygulayabilirsiniz. Bu durumda, sıfır veya daha fazla numaralandırma değeri listesi aynı anda gönderilebilir veya alınabilir.  
  
 Bunu yapmak için, <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bayrak numaralandırmasında uygulayın ve sonra iki üsse olan tüm üyeleri <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliğiyle işaretleyin. Bayrak numaralandırması kullanmak için, ilerlemeyi 2 ' nin (örneğin, 1, 2, 4, 8, 16, 32, 64) kesintisiz bir dizi olması gerektiğini unutmayın.  
  
 Bir bayrağın numaralandırma değerini göndermek için aşağıdaki adımlar geçerlidir:  
  
1. Sayısal değerle eşlenen bir numaralandırma üyesi ( <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği uygulanmış olan) bulmaya çalışır. Bulunursa, yalnızca o üyeyi içeren bir liste gönderin.  
  
2. Toplamın her bir bölümüyle eşlenen numaralandırma üyeleri (her biri uygulanmış olan özniteliği) gibi bir toplama göre sayısal değeri kesmeyi deneyin <xref:System.Runtime.Serialization.EnumMemberAttribute> . Tüm bu üyelerin listesini gönderin. Bu tür bir toplamı bulmak için *doyumsuz algoritmasının* kullanıldığını ve bu nedenle söz konusu toplamın mevcut olsa bile nerede bulunduğunu garanti etmediğini unutmayın. Bu sorundan kaçınmak için, numaralandırma üyelerinin sayısal değerlerinin ikiye üsleri olduğundan emin olun.  
  
3. Yukarıdaki iki adım başarısız olursa ve sayısal değer sıfır değilse, oluşturun <xref:System.Runtime.Serialization.SerializationException> . Sayısal değer sıfırsa boş listeyi gönderin.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki numaralandırma örneği bir bayrak işleminde kullanılabilir.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Aşağıdaki örnek değerler belirtilen şekilde serileştirilir.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Veri Anlaşmalarını Kullanma](using-data-contracts.md)
- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](specifying-data-transfer-in-service-contracts.md)
