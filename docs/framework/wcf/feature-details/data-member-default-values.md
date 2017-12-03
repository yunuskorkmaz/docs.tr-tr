---
title: "Veri Üyesi Varsayılan Değerler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c7d6aa8d695dd6fc79b23e6cbb69bf523ef680f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="data-member-default-values"></a>Veri Üyesi Varsayılan Değerler
İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], türlerine sahip bir kavramı *varsayılan değerlerin*. Örneğin, varsayılan değer tüm başvuru türündeki `null`, ve isteğe bağlı olarak bir tamsayı türü için sıfır olduğunda. Varsayılan değer olarak ayarlandığında serileştirilmiş verilerinden bir veri üyesi atlamak için bazen istenen bir durumdur. Üye varsayılan değeri olduğundan, gerçek bir değer serileştirilmesi değil; Bu performans avantajı vardır.  
  
 Serileştirilmiş veriler üyeden atlamak için ayarlanmış <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğini `false` (varsayılan `true`).  
  
> [!NOTE]
>  Ayarlamanız gerekir <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliğine `false` Bunu yapmak için belirli bir gereksiniminiz varsa, ayarlamayı birlikte çalışabilirliğini ya da veri boyutunu azaltma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod birkaç üyeleriyle olan <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> kümesine `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Bu sınıfın bir örneğini serileştirilmiş, sonucu şu şekildedir: `employeeName` ve `employeeID` serileştirilir. Null değeri `employeeName` ve sıfır değeri `employeeID` açıkça serileştirilmiş veriler bir parçasıdır. Ancak, `position`, `salary`, ve `bonus` üyeleri sıralanmış değildir. Son olarak, `targetSalary` her zamanki gibi rağmen serileştirilmiş <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliği ayarlanmış `false`, çünkü 57800 .NET varsayılan değeri sıfıra eşit bir tamsayı eşleşmiyor.  
  
### <a name="xml-representation"></a>XML gösterimi  
 Önceki örnekte XML olarak serileştirilmiş, temsili aşağıdakine benzer.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 `xsi:nil` Bir null değer açıkça göstermek için birlikte çalışabilir bir yol sağlar World Wide Web Konsorsiyumu (W3C) XML Şeması örnek ad alanındaki özel bir öznitelik bir özniteliktir. Hiçbir bilgi hiç konum, maaş ve ek veri üyeleri hakkında XML yoktur. Alan uçta olarak çevirebilir `null`, sıfır, ve `null`sırasıyla. Bir üçüncü taraf kaldırıcı bu deseni önerilmez neden olan doğru yorumlama yapabilen garantisi yoktur. <xref:System.Runtime.Serialization.DataContractSerializer> Sınıfı her zaman eksik değerleri için doğru yorumlama seçer.  
  
### <a name="interaction-with-isrequired"></a>Isrequired ile etkileşimi  
 ' Da anlatıldığı gibi [veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğine sahip bir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği (varsayılan `false`). Özelliği, bu seri durumdan çıkarılmakta olan, verilen veri üyesi duruma getirilmiş verilerde mevcut olması gerekip gerekmediğini belirtir. Varsa `IsRequired` ayarlanır `true`, (belirten bir değer bulunmalıdır) ve <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ayarlanır `false` (belirtir. değer, varsayılan değere ayarlarsanız mevcut olmamalıdır), bu veri üyesi varsayılan değerleri olamaz sonuçları çelişkili olacağından seri. Böyle bir veri üyesi varsayılan değer olarak ayarlanırsa (genellikle `null` veya sıfır) ve bir seri hale getirme girişiminde, <xref:System.Runtime.Serialization.SerializationException> atılır.  
  
### <a name="schema-representation"></a>Şema gösterimi  
 Veri üyeleri XML Şeması Tanım Dili (XSD) şema gösterimini ayrıntılarını zaman `EmitDefaultValue` özelliği ayarlanmış `false` ele alınmıştır [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Ancak, kısa bir genel bakış verilmiştir:  
  
-   Zaman <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ayarlanır `false`, özel ek açıklama olarak şemada gösterilir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Bu bilgileri temsil eden birlikte çalışabilir yolu yoktur. Şemadaki "varsayılan" özniteliği özellikle bu amaç için kullanılan değil `minOccurs` özniteliği yalnızca etkilenen <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> ayarı ve `nillable` özniteliği, yalnızca veri üyesi türü tarafından etkilenir.  
  
-   Şemada kullanmak üzere gerçek varsayılan değeri yok. Bu öğe eksik uygun şekilde yorumlamaya kadar alıcı uç noktadır.  
  
 Şema alma <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> özelliği ayarlanmış otomatik olarak `false` her [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-belirtilen özel ek açıklama önceden algılandı. Ayrıca ayarlanır `false` başvuru türleri için `nillable` özelliğini `false` kullanırken sık oluşan özel birlikte çalışabilirlik senaryoları desteklemek için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web Hizmetleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>
