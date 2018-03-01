---
title: "Veri Sözleşmelerinde Numaralandırma Türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7989996f7ed64ba4b85ddc1ca01538ec05e99e1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="enumeration-types-in-data-contracts"></a>Veri Sözleşmelerinde Numaralandırma Türleri
Numaralandırmalar veri sözleşmesi modelinde ifade edilebilir. Bu konuda programlama modeli açıklayan birkaç örneklerle anlatılmaktadır.  
  
## <a name="enumeration-basics"></a>Numaralandırma temelleri  
 Numaralandırma türleri veri sözleşmesi modelde kullanmak için bir yoldur uygulamak için <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik türü. Ardından uygulamalısınız <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği her üyesine veri sözleşmede eklenmesi gerekir.  
  
 Aşağıdaki örnekte, iki sınıf gösterir. İlk numaralandırma kullanır ve ikinci numaralandırması tanımlar.  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 Örneği `Car` sınıfı gönderilen ya da yalnızca alınan `condition` alan değerlerden birine ayarlanır `New`, `Used`, veya `Rental`. Varsa `condition` olan `Broken` veya `Stolen`, <xref:System.Runtime.Serialization.SerializationException> atılır.  
  
 Kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute> özellikleri (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ve <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) numaralandırma veri sözleşmeleri için her zamanki gibi.  
  
### <a name="enumeration-member-values"></a>Numaralandırma üye değerleri  
 Genellikle veri sözleşmesi Numaralandırma üye adları, sayısal değerleri içerir. Ancak, ne zaman verileri kullanarak sözleşme modeli, alma tarafı ise bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, dışarı aktarılan şema sayısal değerleri korur. Bu durum kullanırken olmadığını unutmayın [XmlSerializer sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
 Önceki örnekte, `condition` ayarlanır `Used` ve verileri seri için sonuçta elde edilen XML XML'dir `<condition>Used</condition>` ve `<condition>1</condition>`. Bu nedenle, aşağıdaki veri sözleşmesi veri sözleşmesi eşdeğerdir `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 Örneğin, kullanabileceğiniz `CarConditionEnum` Gönderen tarafında ve `CarConditionWithNumbers` alan tarafta. Gönderen tarafı için "1" değeri kullansa `Used` ve alma tarafı kullandığı değer "20," XML gösterimi `<condition>Used</condition>` iki tarafı için.  
  
 Veri sözleşmesi dahil edilecek uygulamalısınız <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği. İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], aynı zamanda tüm numaralandırması için varsayılan değer olan bir numaralandırma için her zaman özel değeri 0 (sıfır) uygulayabilirsiniz. Ancak, sıfır değeri seri hale getirilemiyor ile işaretli değilse bu özel bile <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği.  
  
 Bu iki özel durum vardır:  
  
-   Bayrak numaralandırmalar (Bu konunun ilerleyen bölümlerinde açıklanmıştır).  
  
-   Numaralandırma veri üyeleriyle <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliğini `false` (; Bu durumda sıfır değeri olan numaralandırma atlanırsa serileştirilmiş veriler).  
  
### <a name="customizing-enumeration-member-values"></a>Numaralandırma üye değerlerinin özelleştirme  
 Veri sözleşmesi parçası kullanarak form Numaralandırma üye değeri özelleştirebilirsiniz <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> özelliğinin <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği.  
  
 Örneğin, aşağıdaki veri sözleşmesi ayrıca veri sözleşmesi eşdeğerdir `CarConditionEnum`.  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 Serileştirilmiş zaman değerini `PreviouslyOwned` XML gösterimi yok `<condition>Used</condition>`.  
  
## <a name="simple-enumerations"></a>Basit numaralandırmaları  
 Ayrıca, numaralandırma türleri seri hale getirebilir <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği değil uygulandı. Bu tür Numaralandırma türleri kabul edilir tam olarak daha önce açıklandığı gibi durumlar dışında her üye (, yok <xref:System.NonSerializedAttribute> uygulanan öznitelik) kabul edilir gibi <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği uygulandı. Örneğin, aşağıdaki numaralandırma önceki eşdeğer bir veri sözleşmesi örtük olarak sahip `CarConditionEnum` örnek.  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 Sabit veri sözleşme adına ve ad alanı ve Numaralandırma üye değerlerinin özelleştirmek gerekmediğinde basit numaralandırmalar kullanabilirsiniz.  
  
#### <a name="notes-on-simple-enumerations"></a>Basit numaralandırmalar ile ilgili notlar  
 Uygulama <xref:System.Runtime.Serialization.EnumMemberAttribute> basit numaralandırmalar özniteliğine etkisi yoktur.  
  
 Desteklemediğini fark etmez <xref:System.SerializableAttribute> öznitelik, numaralandırma uygulanır.  
  
 Olgu, <xref:System.Runtime.Serialization.DataContractSerializer> sınıf uyar <xref:System.NonSerializedAttribute> numaralandırma üyelerine uygulanan öznitelik davranışından farklıdır <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Bu serileştiricileri her ikisi de Yoksay <xref:System.NonSerializedAttribute> özniteliği.  
  
## <a name="flag-enumerations"></a>Bayrak numaralandırmaları  
 Uygulayabileceğiniz <xref:System.FlagsAttribute> özniteliği numaralandırmalar için. Bu durumda, sıfır veya daha fazla numaralandırma değerlerinin listesini gönderilebilecek veya aynı anda aldı.  
  
 Bunu yapmak için uygulama <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bayrak sabit ve iki tabanların tüm üyeleri işaretlemek <xref:System.Runtime.Serialization.EnumMemberAttribute> özniteliği. Bayrak sabit kullanmak için ilerlemeyi 2 (örneğin, 1, 2, 4, 8, 16, 32, 64) tabanların kesintisiz bir dizi olması gerektiğini unutmayın.  
  
 Bir bayrağın numaralandırma değeri göndermek için aşağıdaki adımları uygulayın:  
  
1.  Bir numaralandırma üyesine bulmaya (ile <xref:System.Runtime.Serialization.EnumMemberAttribute> uygulanan öznitelik) sayısal değer eşler. Varsa bulunan, yalnızca bu üyeyi içeren bir liste göndermek.  
  
2.  Vardır numaralandırma üyeleri, sayısal değer toplam kesme girişimi (her biri <xref:System.Runtime.Serialization.EnumMemberAttribute> uygulanan öznitelik) toplamı her bir parçasını eşleyin. Bu tüm üyelerin listesi gönderin. Unutmayın *doyumsuz algoritması* böyle bir toplam bulmak için kullanılır ve bu nedenle, mevcut olsa bile, bu tür bir toplam bulunan garantisi yoktur. Bu sorunu önlemek için numaralandırma üyeleri sayısal değerleri iki tabanların olduğundan emin olun.  
  
3.  Önceki iki adımı başarısız ve sayısal değerin sıfır ise, throw bir <xref:System.Runtime.Serialization.SerializationException>. Sayısal değer sıfır ise, boş bir liste gönderin.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki numaralandırma örnek bayrağı işlemde kullanılabilir.  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 Aşağıdaki örnek değerler belirtildiği gibi serileştirilir.  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
