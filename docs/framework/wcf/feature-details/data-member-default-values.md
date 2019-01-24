---
title: Veri Üyesi Varsayılan Değerler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: 30836f7f1cbf742c621254ef92314d20a4fffd83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715083"
---
# <a name="data-member-default-values"></a>Veri Üyesi Varsayılan Değerler
İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], türlerine sahip bir kavramı *varsayılan değerler*. Örneğin, varsayılan değer: bir başvuru türü için `null`, ve isteğe bağlı olarak bir tamsayı türü için sıfır ise. Seri hale getirilmiş verilerden veri üyesi varsayılan değerine ayarlandığında atlamak için zaman zaman istenen bir durumdur. Varsayılan değer üyesine sahip olduğundan, gerçek bir değer seri hale yok; Bu, bir performans avantajı vardır.  
  
 Seri hale getirilmiş veri üyesi atlanacak Ayarla <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğini `false` (varsayılan değer `true`).  
  
> [!NOTE]
>  Ayarlamalısınız <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliğini `false` Bunu yapmak için belirli bir gereksiniminiz varsa, örneğin birlikte çalışabilirliğini ya da veri boyutunu azaltma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod ile birkaç üyelere sahip <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> kümesine `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Bu sınıfın örneğini serileştirilmiş, sonuç şu şekilde olur: `employeeName` ve `employeeID` serileştirilir. Null değeri `employeeName` ve sıfır değeri `employeeID` serileştirilmiş veriler açıkça parçasıdır. Ancak, `position`, `salary`, ve `bonus` üyeleri sıralanmış değildir. Son olarak, `targetSalary` zamanki olsa bile seri <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliği `false`, 57800 .NET varsayılan değeri sıfıra eşit bir tamsayı ile eşleşmiyor.  
  
### <a name="xml-representation"></a>XML gösterimi  
 Önceki örnekte, XML'e seri, aşağıdakine benzer bir gösterimidir.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil` Açıkça null değeri temsil etmek için birlikte çalışabilen bir yol sağlar World Wide Web Consortium (W3C) XML Şeması örneği ad alanında bir özel özniteliği bir özniteliktir. Hiçbir bilgi hiç konumunu, maaş ve ek veri üyeleri hakkında XML'de unutmayın. Alan uçta olarak yorumlayabilir `null`, sıfır, ve `null`sırasıyla. Bir üçüncü taraf seri durumdan çıkarıcı bu düzen önerilmez neden olan doğru yorumu yapabilen bir garanti yoktur. <xref:System.Runtime.Serialization.DataContractSerializer> Sınıfı her zaman eksik değerleri için doğru yorumu seçer.  
  
### <a name="interaction-with-isrequired"></a>Isrequired etkileşim  
 Bölümünde açıklandığı gibi [veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğine sahip bir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği (varsayılan değer `false`). Özelliği, seri durumdan verilen veri üyesi seri duruma getirilmiş verilerde mevcut olması gerekip gerekmediğini gösterir. Varsa `IsRequired` ayarlanır `true`, (belirten bir değer bulunmalıdır) ve <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ayarlanır `false` (belirtir. değer varsayılan değerine ayarlanırsa mevcut olmamalıdır), varsayılan değerleri bu veri üyesi olamaz sonuçları çelişkili olacağından seri. Böyle bir veri üyesi varsayılan değerine ayarlanmış olup olmadığını (genellikle `null` ya da sıfır) ve bir seri hale getirme denemesi, <xref:System.Runtime.Serialization.SerializationException> oluşturulur.  
  
### <a name="schema-representation"></a>Şema gösterimi  
 Veri üyeleri XML Şeması Tanım Dili (XSD) şeması gösterimi ayrıntılarını olduğunda `EmitDefaultValue` özelliği `false` ele alınmıştır [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Ancak, kısa bir özeti verilmiştir:  
  
-   Zaman <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ayarlanır `false`, Windows Communication Foundation (WCF) için belirli bir ek açıklama yer alan şemada gösterilir. Bu bilgileri temsil eden birlikte çalışabilen bir yolu yoktur. Özellikle, şema "varsayılan" özniteliği, bu amaç için kullanılmaz `minOccurs` özniteliği yalnızca etkilenen <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> ayarı ve `nillable` özniteliği, türü yalnızca veri üyesi tarafından etkilenir.  
  
-   Şemada kullanılacak gerçek varsayılan değeri yok. Bu, uygun şekilde eksik bir öğesini yorumlamak için en fazla alıcı uç noktadır.  
  
 Şema içeri aktarma, <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> otomatik olarak ayarlanırsa `false` bahsedilen WCF özgü açıklama daha önce algılanır. Ayrıca ayarlanmış `false` olan başvuru türleri için `nillable` özelliğini `false` tüketildiğinde sık gerçekleşen belirli bir birlikte çalışabilirlik senaryolarını desteklemek üzere [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
