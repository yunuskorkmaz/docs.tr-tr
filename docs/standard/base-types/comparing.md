---
title: ".NET dizeleri karşılaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET Framework], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a9c2597ed2321c7494eaf44c3c43c2edc4df1952
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="comparing-strings-in-net"></a>.NET dizeleri karşılaştırma
.NET dizeleri değerleri karşılaştırmak için çeşitli yöntemler sağlar. Aşağıdaki tabloda listelenmekte ve değer karşılaştırması yöntemleri açıklar.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|İki dizeyi değerlerini karşılaştırır. Bir Integer değeri döndürür.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|İki dizeyi yerel kültür dikkate almaksızın karşılaştırır. Bir Integer değeri döndürür.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Geçerli dize nesnesi başka bir dizeye karşılaştırır. Bir Integer değeri döndürür.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Bir dize geçirilen dize ile başlayan olup olmadığını belirler. Bir Boole değeri döndürür.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Bir dize geçirilen dizesiyle biten olup olmadığını belirler. Bir Boole değeri döndürür.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|İki dizeyi aynı olup olmadığını belirler. Bir Boole değeri döndürür.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Bir karakter ya da dize, İncelemekte olduğunuz dize başından başlayarak dizin konumunu döndürür. Bir Integer değeri döndürür.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Bir karakter ya da dize, İncelemekte olduğunuz dizesinin sonundan başlayarak dizin konumunu döndürür. Bir Integer değeri döndürür.|  
  
## <a name="compare"></a>Karşılaştırma  
 Statik <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi iki dizeleri karşılaştırma, tam bir yol sağlar. Bu yöntem culturally bilmez. İki dizeyi veya iki dizeleri alt dizeleri karşılaştırmak için bu işlevi kullanabilirsiniz. Buna ek olarak, aşırı bu şekilde sağlanır veya çalışması ve kültürel farkı dikkate. Aşağıdaki tabloda, bu yöntem döndürebilir üç tamsayı değerleri gösterir.  
  
|Dönüş değeri|Koşul|  
|------------------|---------------|  
|Negatif bir tamsayı|İlk dizesi ikinci dize sıralama düzenini önce gelir.<br /><br /> veya<br /><br /> İlk dize `null`.|  
|0|İlk dizesi ve ikinci dize eşit.<br /><br /> veya<br /><br /> Her iki dizelerdir `null`.|  
|Pozitif bir tamsayı<br /><br /> veya<br /><br /> 1.|İlk dizesi ikinci dizenin sıralama düzenini izler.<br /><br /> veya<br /><br /> İkinci dize `null`.|  
  
> [!IMPORTANT]
>  <xref:System.String.Compare%2A?displayProperty=nameWithType> Yöntemi sıralama veya dizeleri sıralama kullanmak için öncelikle amaçlanmıştır. Kullanılamaz <xref:System.String.Compare%2A?displayProperty=nameWithType> eşitlik için test yöntemi (diğer bir deyişle, açıkça 0 ile hiçbir şekilde mi için dönüş değerini aramak için bir dizedir veya diğer değerinden daha küçük). İki dizeyi eşit olup olmadığını belirlemek için bunun yerine, kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki örnek kullanır <xref:System.String.Compare%2A?displayProperty=nameWithType> iki dizeyi göreli değerlerini belirlemek amacıyla yöntemi.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Bu örnek görüntüler `-1` Konsolu'na.  
  
 Önceki örnekte kültüre duyarlı varsayılan olarak. Kültüre duyarsız dize karşılaştırma yapabilmesi için bir aşırı yüklemesini kullanın <xref:System.String.Compare%2A?displayProperty=nameWithType> sağlayarak kullanılacak kültürü belirtmenize olanak tanır yöntemi bir *kültür* parametresi. Nasıl kullanılacağını gösteren bir örnek için <xref:System.String.Compare%2A?displayProperty=nameWithType> kültüre duyarsız bir karşılaştırma yapmak için yöntemi bkz [kültüre duyarsız dize karşılaştırmalarını gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal  
 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Yöntemi yerel kültür düşünmeden iki dize nesnelerini karşılaştırır. Bu yöntemin dönüş değerleri tarafından döndürülen değer aynıdır **karşılaştırmak** önceki tabloda yöntemi.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Yöntemi sıralama veya dizeleri sıralama kullanmak için öncelikle amaçlanmıştır. Kullanılamaz <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> eşitlik için test yöntemi (diğer bir deyişle, açıkça 0 ile hiçbir şekilde mi için dönüş değerini aramak için bir dizedir veya diğer değerinden daha küçük). İki dizeyi eşit olup olmadığını belirlemek için bunun yerine, kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki örnek kullanır **CompareOrdinal** iki dize değerleri karşılaştırmak için yöntem.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Bu örnek görüntüler `-32` Konsolu'na.  
  
## <a name="compareto"></a>CompareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Yöntemi geçerli dize nesnesi başka bir dize veya nesne yalıtır dize karşılaştırır. Bu yöntemin dönüş değerleri tarafından döndürülen değer aynıdır <xref:System.String.Compare%2A?displayProperty=nameWithType> önceki tabloda yöntemi.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Yöntemi sıralama veya dizeleri sıralama kullanmak için öncelikle amaçlanmıştır. Kullanılamaz <xref:System.String.CompareTo%2A?displayProperty=nameWithType> eşitlik için test yöntemi (diğer bir deyişle, açıkça 0 ile hiçbir şekilde mi için dönüş değerini aramak için bir dizedir veya diğer değerinden daha küçük). İki dizeyi eşit olup olmadığını belirlemek için bunun yerine, kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki örnek kullanır <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Karşılaştırılacak yöntemi `string1` nesnesini `string2` nesne.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Bu örnek görüntüler `-1` Konsolu'na.  
  
 Tüm aşırı <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi varsayılan kültüre duyarlı ve büyük küçük harfe duyarlı karşılaştırmalar gerçekleştirin. Bu yöntem, hiçbir aşırı kültüre duyarsız bir karşılaştırma gerçekleştirmenize olanak sağlanır. Kodu daha anlaşılır olması için kullanmanızı öneririz **String.Compare** yöntemi bunun yerine, belirtme <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> kültüre duyarlı işlemleri için veya <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> kültüre duyarsız işlemleri için. Nasıl kullanılacağını gösteren örnekleri için **String.Compare** kültüre duyarlı hem kültüre duyarsız karşılaştırma yapmak için yöntemi bkz [gerçekleştirme kültüre duyarsız dize karşılaştırmalarını](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Eşittir  
 **String.Equals** yöntemi, iki dizeyi aynı olup olmadığını kolayca belirleyebilir. Büyük küçük harfe duyarlı bu yöntem bir **true** veya **false** Boole değeri. Bu varolan bir sınıftan sonraki örnekte gösterildiği gibi kullanılabilir. Aşağıdaki örnek kullanır **eşittir** bir dize nesnesi "Hello World" ifadesini içerip içermediğini belirlemek için yöntem.  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Bu örnek görüntüler `True` Konsolu'na.  
  
 Bu yöntem, bir statik yöntem olarak da kullanılabilir. Aşağıdaki örnek, bir statik yöntem kullanılarak iki dize nesnelerini karşılaştırır.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Bu örnek görüntüler `True` Konsolu'na.  
  
## <a name="startswith-and-endswith"></a>StartsWith ve EndsWith  
 Kullanabileceğiniz **String.StartsWith** bir dize nesnesi başka bir dize kapsayan karakterle başlar olup olmadığını belirlemek amacıyla yöntemi. Büyük küçük harfe duyarlı bu yöntem **true** geçerli dize nesnesi geçirilen dizesi ile başlayıp başlamadığını ve **false** mevcut değilse. Aşağıdaki örnek, bir dize nesnesi "Hello"ifadesini ile başlayıp başlamadığını belirlemek için bu yöntemi kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Bu örnek görüntüler `True` Konsolu'na.  
  
 **String.EndsWith** yöntemi geçerli dize nesnesi sonunda mevcut karakterleri geçirilen bir dizeye karşılaştırır. Ayrıca, bir Boole değeri döndürür. Aşağıdaki örneği kullanarak bir dize sonu denetler **EndsWith** yöntemi.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Bu örnek görüntüler `False` Konsolu'na.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf ve lastIndexOf  
 Kullanabileceğiniz **String.IndexOf** dize içinde belirli bir karakterin ilk oluşum konumunu belirlemek için yöntem. Büyük küçük harfe duyarlı bu yöntem bir dize başlangıcından sayarak başlatır ve sıfır tabanlı dizini kullanılarak geçirilen bir karakterin konumu döndürür. Karakter bulunamazsa, -1 değeri döndürülür.  
  
 Aşağıdaki örnek kullanır **IndexOf** ilk geçtiği için aranacak yöntem '`l`' bir dizedeki karakter.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Bu örnek görüntüler `2` Konsolu'na.  
  
 **String.LastIndexOf** yöntemi benzer **String.IndexOf** yöntemi, BT'nin dışında dize içinde belirli bir karakterin son oluşum konumunu döndürür. Küçük harfe duyarlıdır ve sıfır tabanlı bir dizin kullanır.  
  
 Aşağıdaki örnek kullanır **lastIndexOf** son a geçişi için aranacak yöntem '`l`' bir dizedeki karakter.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Bu örnek görüntüler `9` Konsolu'na.  
  
 Her iki yöntem ile birlikte kullanıldığında faydalı **String.Remove** yöntemi. Kullanabilirsiniz **IndexOf** veya **lastIndexOf** bir karakterin almak ve bu konuma sağlamak için yöntemleri **kaldırmak** kaldırmak için yöntemi bir karakter veya bu karakteri ile başlayan bir sözcük.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)  
 [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
