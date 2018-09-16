---
title: . NET'te dizeleri karşılaştırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8f126aa5b69c99beae740de261ac3da3c5d2544
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674630"
---
# <a name="comparing-strings-in-net"></a>. NET'te dizeleri karşılaştırma
.NET, dizeleri karşılaştırmak için çeşitli yöntemler sunar. Aşağıdaki tabloda, listeler ve değer karşılaştırma yöntemleri açıklar.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|İki dizenin değerini karşılaştırır. Bir Integer değeri döndürür.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Yerel kültüre bakılmaksızın iki dizeyi karşılaştırır. Bir Integer değeri döndürür.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Geçerli bir dize nesnesi başka bir dizeye karşılaştırır. Bir Integer değeri döndürür.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Bir dize geçirilen dize ile başlayan olup olmadığını belirler. Bir Boolean değer döndürür.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Bir dize geçirilen dize ile bitip bitmediğini belirler. Bir Boolean değer döndürür.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|İki dizenin aynı olup olmadığını belirler. Bir Boolean değer döndürür.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Bir karakter veya dize, İncelemekte olduğunuz dizenin en baştan başlatmayı dizin konumunu döndürür. Bir Integer değeri döndürür.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Bir karakter veya dize, İncelemekte olduğunuz dizesinin sonundan başlayarak dizin konumunu döndürür. Bir Integer değeri döndürür.|  
  
## <a name="compare"></a>{1&gt;Karşılaştır&lt;1}  
 Statik <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi, iki dizeyi karşılaştıran kapsamlı bir yol sağlar. Bu yöntem duyarlıymış farkındadır. İki dizeyi veya iki dizenin alt dizeleri karşılaştırmak için bu işlevi kullanabilirsiniz. Ayrıca, aşırı yüklemeler, haklısın sağlanır veya çalışması ve kültürel farkı dikkate. Aşağıdaki tabloda, bu yöntem döndürebilir üç tamsayı değerleri gösterir.  
  
|Dönüş değeri|Koşul|  
|------------------|---------------|  
|Negatif bir tamsayı|Birinci dize ikinci dize sıralama düzeninde önce gelir.<br /><br /> veya<br /><br /> İlk dize `null`.|  
|0|İlk dize ve ikinci dize eşit olur.<br /><br /> veya<br /><br /> Her iki dizelerdir `null`.|  
|Pozitif bir tamsayı<br /><br /> veya<br /><br /> 1.|Birinci dize ikinci dize sıralama düzenini izler.<br /><br /> veya<br /><br /> İkinci dize `null`.|  
  
> [!IMPORTANT]
>  <xref:System.String.Compare%2A?displayProperty=nameWithType> Yöntemi için sıralama veya dizeleri sıralama sırasında kullanılacak amaçlanmaktadır. Kullanmamalısınız <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi eşitlik için test etmek için (diğer bir deyişle, 0 ile hiçbir şekilde mi için dönüş değeri açıkça aramak için bir dizedir küçük veya büyük). İki dizenin eşit olup olmadığını belirlemek için bunun yerine, kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki örnekte <xref:System.String.Compare%2A?displayProperty=nameWithType> iki dizenin göreli değerlerini belirlemek için yöntemi.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Bu örnek görüntüler `-1` konsola.  
  
 Yukarıdaki örnekte, kültüre duyarlı varsayılan olarak. Kültüre duyarsız dize karşılaştırma yapmak için bir aşırı yüklemesini kullanmanız <xref:System.String.Compare%2A?displayProperty=nameWithType> sağlanarak kullanılacak kültürü belirtmenize olanak tanıyan yöntemi bir *kültür* parametresi. Nasıl kullanılacağını gösteren bir örnek <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemi kültüre duyarsız bir karşılaştırma gerçekleştirmek için bkz. [kültüre duyarsız dize karşılaştırmalarını gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal  
 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Yöntemi iki dize nesnelerinin yerel kültürü düşünmeden karşılaştırır. Bu yöntemin dönüş değerleri tarafından döndürülen değerlerin aynı **karşılaştırma** önceki tabloda yöntemi.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> Yöntemi için sıralama veya dizeleri sıralama sırasında kullanılacak amaçlanmaktadır. Kullanmamalısınız <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> yöntemi eşitlik için test etmek için (diğer bir deyişle, 0 ile hiçbir şekilde mi için dönüş değeri açıkça aramak için bir dizedir küçük veya büyük). İki dizenin eşit olup olmadığını belirlemek için bunun yerine, kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki örnekte **CompareOrdinal** iki dize değerlerini karşılaştırmak için yöntemi.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Bu örnek görüntüler `-32` konsola.  
  
## <a name="compareto"></a>compareTo  
 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Yöntemi başka bir dize veya nesne geçerli bir dize nesnesi kapsülleyen dizeyi karşılaştırır. Bu yöntemin dönüş değerleri tarafından döndürülen değerlerin aynı <xref:System.String.Compare%2A?displayProperty=nameWithType> önceki tabloda yöntemi.  
  
> [!IMPORTANT]
>  <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Yöntemi için sıralama veya dizeleri sıralama sırasında kullanılacak amaçlanmaktadır. Kullanmamalısınız <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi eşitlik için test etmek için (diğer bir deyişle, 0 ile hiçbir şekilde mi için dönüş değeri açıkça aramak için bir dizedir küçük veya büyük). İki dizenin eşit olup olmadığını belirlemek için bunun yerine, kullanın <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> yöntemi.  
  
 Aşağıdaki örnekte <xref:System.String.CompareTo%2A?displayProperty=nameWithType> Karşılaştırılacak yöntemi `string1` nesnesini `string2` nesnesi.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Bu örnek görüntüler `-1` konsola.  
  
 Tüm aşırı yüklemeler, <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemi varsayılan olarak kültüre duyarlı ve büyük küçük harfe duyarlı karşılaştırmalar gerçekleştirin. Kültüre duyarsız bir karşılaştırma gerçekleştirmek için izin yok Bu yöntemin aşırı sağlanır. Kod netliği için biz kullanmanızı öneririz. **String.Compare** yöntemi bunun yerine, belirtme <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> kültüre duyarlı işlemler için veya <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> kültüre duyarsız işlemleri için. Nasıl kullanılacağını gösteren örnekler için **String.Compare** yöntemi kültüre duyarlı hem kültüre duyarsız karşılaştırmalar yapmak için bkz. [gerçekleştirme kültüre duyarsız dize karşılaştırmalarını](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Eşittir  
 **String.Equals** yöntemi, iki dizenin aynı olup olmadığını kolayca belirleyebilirsiniz. Bu büyük/küçük harfe yöntemi döndürür bir **true** veya **false** Boole değeri. Bu varolan bir sınıftan sonraki örnekte gösterildiği gibi kullanılabilir. Aşağıdaki örnekte **eşittir** bir dize nesnesi "Hello World" ifadesini içerip içermediğini belirlemek için yöntemi.  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Bu örnek görüntüler `True` konsola.  
  
 Bu yöntem, statik bir yöntem olarak da kullanılabilir. Aşağıdaki örnek, statik bir yöntem kullanılarak iki dize nesneleri karşılaştırır.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Bu örnek görüntüler `True` konsola.  
  
## <a name="startswith-and-endswith"></a>StartsWith ve EndsWith  
 Kullanabileceğiniz **String.StartsWith** bir dize nesnesi başka bir dize çevreleyen aynı karakterle başlayan olup olmadığını belirlemek için yöntemi. Büyük/küçük harfe döner **true** geçerli dize nesnesine geçirilen dizesiyle başlayıp başlamadığını ve **false** Aksi takdirde. Aşağıdaki örnek, bir dize nesnesi "Hello" ile başlayıp başlamadığını belirlemek için bu yöntemi kullanır.  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Bu örnek görüntüler `True` konsola.  
  
 **String.EndsWith** yöntemi geçirilen bir dize geçerli bir dize nesnesi sonunda mevcut karakterleri karşılaştırır. Ayrıca, bir Boole değeri döndürür. Aşağıdaki örnek bir dize kullanarak sonuna denetler **EndsWith** yöntemi.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Bu örnek görüntüler `False` konsola.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf ve lastIndexOf  
 Kullanabileceğiniz **String.IndexOf** dize içinde belirli bir karakterin ilk geçtiği konumu belirlemek için yöntemi. Büyük/küçük harfe bu yöntem bir dize başından saymaya başlar ve sıfır tabanlı dizin kullanılarak geçirilen bir karakter konumunu döndürür. Karakter bulunamazsa, – 1 değerini döndürülür.  
  
 Aşağıdaki örnekte **IndexOf** ilk geçtiği için aranacak yöntem '`l`' bir dizedeki karakter.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Bu örnek görüntüler `2` konsola.  
  
 **String.lastIndexOf** yöntemi benzer **String.IndexOf** yöntemi dışında olan belirli bir karakter dize içinde son oluşum konumunu döndürür. Bu büyük/küçük harfe ve sıfır tabanlı dizini kullanır.  
  
 Aşağıdaki örnekte **lastIndexOf** son oluşumu için aranacak yöntem '`l`' bir dizedeki karakter.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Bu örnek görüntüler `9` konsola.  
  
 Her iki yöntem birlikte kullanıldığında faydalı **String.Remove** yöntemi. Kullanabilirsiniz **IndexOf** veya **lastIndexOf** bir karakterin konumu almak ve sonra o konuma sağlamak için yöntemleri **Kaldır** kaldırmak için yöntemi bir karakter veya söz konusu karakteri ile başlayan bir sözcük.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)  
- [Kültüre Duyarsız Dize İşlemlerini Gerçekleştirme](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [Sıralama ağırlık tablolar (için Windows üzerinde .NET)](https://www.microsoft.com/en-us/download/details.aspx?id=10921)
- [Varsayılan Unicode Harmanlama öğesi tablosu (Linux ve Macos'ta .NET Core)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
