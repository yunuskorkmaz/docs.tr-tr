---
title: Veri Üyesi Varsayılan Değerler
description: .NET Framework bir varsayılan değere sahip olduğunda serileştirilmiş verilerden bir veri üyesini nasıl atleyeceğinizi öğrenin. WCF, Varsayılanı serileştirmez performansı iyileştirebilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: 97946a6b7da14efdcb5229b4cc5d0799eb8d7723
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247383"
---
# <a name="data-member-default-values"></a>Veri Üyesi Varsayılan Değerler
.NET Framework, türlerin *varsayılan değer*kavramıdır. Örneğin, herhangi bir başvuru türü için varsayılan değer `null` , ve bir tamsayı türü için sıfırdır. Zaman zaman, varsayılan değerine ayarlandığında serileştirilmiş verilerden bir veri üyesini atlamak tercih edilir. Üyenin varsayılan bir değeri olduğundan, gerçek değerin serileştirilmesi gerekmez; Bunun bir performans avantajı vardır.  
  
 Seri hale getirilmiş verilerden bir üyeyi atlamak için, <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özniteliğinin özelliğini olarak ayarlayın <xref:System.Runtime.Serialization.DataMemberAttribute> `false` (varsayılan olarak `true` ).  
  
> [!NOTE]
> <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>Özelliği, `false` birlikte çalışabilirlik veya veri boyutu azaltma gibi belirli bir ihtiyacı varsa olarak ayarlamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, olarak ayarlanmış birkaç üyeye sahiptir <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> `false` .  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Bu sınıfın bir örneği serileştirildiğinden, sonuç aşağıdaki gibidir: `employeeName` ve `employeeID` serileştirilir. İçin null değeri `employeeName` ve sıfır değeri, `employeeID` seri hale getirilmiş verilerin açıkça bir parçasıdır. Ancak,, `position` `salary` ve `bonus` üyeleri serileştirilmez. Son olarak, `targetSalary` özelliği olarak ayarlanmış olsa bile, her zamanki gibi serileştirilir, <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> `false` çünkü 57800, sıfır olan bir tamsayı için .NET varsayılan değeri ile eşleşmez.  
  
### <a name="xml-representation"></a>XML temsili  
 Önceki örnek XML 'e serileştirilse, temsili aşağıdakine benzer.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil`Özniteliği, bir null değeri açıkça temsil etmek için birlikte çalışabilen bir yol sağlayan World Wide Web Konsorsiyumu (W3C) XML şema örneği ad alanındaki özel bir özniteliktir. XML 'de konum, maaş ve ek veri üyeleri hakkında hiçbir bilgi bulunmadığını unutmayın. Alma ucu bunları `null` sırasıyla, sıfır ve olarak yorumlayabilir `null` . Üçüncü taraf seri hale getiricinin doğru yorumu yapabileceğinizin garantisi yoktur, bu da bu düzenin neden önerilmez. <xref:System.Runtime.Serialization.DataContractSerializer>Sınıf, eksik değerler için her zaman doğru yorumu seçer.  
  
### <a name="interaction-with-isrequired"></a>IsRequired ile etkileşim  
 [Veri anlaşması sürümü oluşturma](data-contract-versioning.md)bölümünde açıklandığı gibi, <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğinde bir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği vardır (varsayılan olarak `false` ). Özelliği, seri durumdan çıkarılmakta olan serileştirilmiş verilerde verilen veri üyesinin mevcut olup olmadığını gösterir. `IsRequired`, Olarak ayarlanmışsa `true` (bir değerin mevcut olması gerektiğini belirtir) ve <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> olarak ayarlanır `false` (değerin varsayılan değerine ayarlandıysa olmaması gerektiğini belirten), bu veri üyesinin varsayılan değerleri, sonuçlar çelişkili olacağından serileştirilemiyor. Böyle bir veri üyesi varsayılan değerine ayarlandıysa (genellikle `null` veya sıfır) ve bir serileştirme denendiğinde, bir <xref:System.Runtime.Serialization.SerializationException> atılır.  
  
### <a name="schema-representation"></a>Şema gösterimi  
 `EmitDefaultValue`Özelliği `false` [veri sözleşmesi şema başvurusunda](data-contract-schema-reference.md)açıklandığı zaman, veri üyelerinin XML ŞEMASı tanım dili (xsd) şema gösteriminin ayrıntıları. Bununla birlikte, aşağıdakiler kısaca genel bir bakış verilmiştir:  
  
- , <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> Olarak ayarlandığında `false` , WINDOWS COMMUNICATION FOUNDATION (WCF) için özel bir ek açıklama olarak şemada temsil edilir. Bu bilgileri göstermek için birlikte çalışabilen bir yol yoktur. Özellikle, şemadaki "default" özniteliği bu amaçla kullanılmaz, `minOccurs` özniteliği yalnızca <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> ayarından etkilenir ve `nillable` özniteliği yalnızca veri üyesinin türü tarafından etkilenir.  
  
- Kullanılacak gerçek varsayılan değer şemada yok. Eksik bir öğeyi uygun şekilde yorumlamak için alıcı uç noktaya kadar.  
  
 Şema içeri aktarma işleminde, bu <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özellik, `false` daha önce belirtilen WCF 'ya özgü ek açıklama her zaman otomatik olarak ayarlanır. Ayrıca, `false` `nillable` `false` ASP.NET Web Hizmetleri kullanılırken yaygın olarak oluşan belirli birlikte çalışabilirlik senaryolarını desteklemek için özelliği olarak ayarlanmış başvuru türleri için olarak ayarlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
