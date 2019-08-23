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
ms.openlocfilehash: 17e73ab2aa777ae53f31596fa364a4feac297842
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962925"
---
# <a name="data-member-default-values"></a>Veri Üyesi Varsayılan Değerler
.NET Framework, türlerin *varsayılan değer*kavramıdır. Örneğin, herhangi bir başvuru türü için varsayılan değer `null`, ve bir tamsayı türü için sıfırdır. Zaman zaman, varsayılan değerine ayarlandığında serileştirilmiş verilerden bir veri üyesini atlamak tercih edilir. Üyenin varsayılan bir değeri olduğundan, gerçek değerin serileştirilmesi gerekmez; Bunun bir performans avantajı vardır.  
  
 Seri hale getirilmiş verilerden bir <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> üyeyi atlamak için, <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğinin özelliğini olarak `false` ayarlayın (varsayılan olarak `true`).  
  
> [!NOTE]
> Özelliği, birlikte çalışabilirlik veya veri boyutu azaltma gibi belirli bir ihtiyacı varsaolarakayarlamanızgerekir.`false` <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, olarak <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> `false`ayarlanmış birkaç üyeye sahiptir.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Bu sınıfın bir örneği serileştirildiğinden, sonuç aşağıdaki gibidir: `employeeName` ve `employeeID` serileştirilir. İçin null değeri `employeeName` ve sıfır `employeeID` değeri, seri hale getirilmiş verilerin açıkça bir parçasıdır. Ancak,, ve`bonus` üyeleri serileştirilmez. `position` `salary` Son olarak `targetSalary` , <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliği olarak ayarlanmış `false`olsa bile, her zamanki gibi serileştirilir, çünkü 57800, sıfır olan bir tamsayı için .NET varsayılan değeri ile eşleşmez.  
  
### <a name="xml-representation"></a>XML temsili  
 Önceki örnek XML 'e serileştirilse, temsili aşağıdakine benzer.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil` Özniteliği, bir null değeri açıkça temsil etmek için birlikte çalışabilen bir yol sağlayan World Wide Web Konsorsiyumu (W3C) XML şema örneği ad alanındaki özel bir özniteliktir. XML 'de konum, maaş ve ek veri üyeleri hakkında hiçbir bilgi bulunmadığını unutmayın. Alma ucu bunları sırasıyla, sıfır ve `null` `null`olarak yorumlayabilir. Üçüncü taraf seri hale getiricinin doğru yorumu yapabileceğinizin garantisi yoktur, bu da bu düzenin neden önerilmez. <xref:System.Runtime.Serialization.DataContractSerializer> Sınıf, eksik değerler için her zaman doğru yorumu seçer.  
  
### <a name="interaction-with-isrequired"></a>IsRequired ile etkileşim  
 [Veri anlaşması sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)bölümünde açıklandığı gibi, <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğinde bir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği vardır (varsayılan `false`olarak). Özelliği, seri durumdan çıkarılmakta olan serileştirilmiş verilerde verilen veri üyesinin mevcut olup olmadığını gösterir. Öğesi olarak `true`ayarlanmışsa (bir değerin mevcut olması gerektiğini belirtir) ve <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> olarak `false` ayarlanır (değerin varsayılan değerine ayarlandıysa, değerin mevcut olmaması gerektiğini gösterir), bu veri üyesinin varsayılan değerleri `IsRequired` sonuçlar çelişkili olacağı için serileştirilmiş. Böyle bir veri üyesi varsayılan değerine ayarlandıysa (genellikle `null` veya sıfır) ve bir serileştirme denendiğinde, bir <xref:System.Runtime.Serialization.SerializationException> atılır.  
  
### <a name="schema-representation"></a>Şema gösterimi  
 `EmitDefaultValue` Özelliği veri`false` [Sözleşmesi Şema başvurusunda](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)açıklandığı zaman, veri üyelerinin XML şeması tanım dili (xsd) şema gösteriminin ayrıntıları. Bununla birlikte, aşağıdakiler kısaca genel bir bakış verilmiştir:  
  
- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> , Olarak`false`ayarlandığında, Windows Communication Foundation (WCF) için özel bir ek açıklama olarak şemada temsil edilir. Bu bilgileri göstermek için birlikte çalışabilen bir yol yoktur. Özellikle, şemadaki "default" özniteliği bu amaçla kullanılmaz, `minOccurs` özniteliği yalnızca <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> ayarından etkilenir ve `nillable` özniteliği yalnızca veri üyesinin türü tarafından etkilenir.  
  
- Kullanılacak gerçek varsayılan değer şemada yok. Eksik bir öğeyi uygun şekilde yorumlamak için alıcı uç noktaya kadar.  
  
 Şema içeri aktarma işleminde, <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> bu özellik, daha önce `false` belirtilen WCF 'ya özgü ek açıklama her zaman otomatik olarak ayarlanır. Ayrıca, ASP.NET Web Hizmetleri `false` kullanılırken yaygın olarak oluşan belirli birlikte `nillable` çalışabilirlik senaryolarını desteklemek `false` için özelliği olarak ayarlanmış başvuru türleri için olarak ayarlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
