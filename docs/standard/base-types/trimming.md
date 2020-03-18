---
title: .NET'te Dizeleri Kırpma ve Çıkarma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: bdbe267bb178e90c0008422e6543a23178c2c4d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159994"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>.NET'te Dizeleri Kırpma ve Çıkarma
Bir cümleyi tek tek sözcüklere ayrıştırıyorsanız, sözcüğün her iki ucunda boş alanlar (beyaz boşluklar olarak da adlandırılır) sözcüklerle sona erebilir. Bu durumda, string'deki belirli bir konumdan herhangi bir sayıda boşluk veya diğer karakteri kaldırmak için **System.String** sınıfındaki kırpma yöntemlerinden birini kullanabilirsiniz. Aşağıdaki tabloda kullanılabilir kırpma yöntemleri açıklanmaktadır.  
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Dize başından ve sonundan bir karakter dizisinde belirtilen beyaz boşlukları veya karakterleri kaldırır.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Dize sonundan bir karakter dizisinde belirtilen karakterleri kaldırır.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Dize başlangıcından bir karakter dizisinde belirtilen karakterleri kaldırır.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Bir dizedeki belirli bir dizin konumundan belirli sayıda karakter kaldırır.|  
  
## <a name="trim"></a>Trim

 Aşağıdaki örnekte gösterildiği gibi <xref:System.String.Trim%2A?displayProperty=nameWithType> yöntemi kullanarak dizenin her iki ucundan beyaz boşlukları kolayca kaldırabilirsiniz.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Ayrıca, bir karakter dizisinde belirttiğiniz karakterleri bir dizebaşından ve sonundan da kaldırabilirsiniz. Aşağıdaki örnek, boşluk karakterlerini, dönemleri ve yıldız yıldızlarını kaldırır.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd

 **String.TrimEnd** yöntemi karakterleri bir dize sonundan kaldırarak yeni bir dize nesnesi oluşturur. Kaldırılacak karakterleri belirtmek için bu yönteme bir dizi karakter aktarılır. Karakter dizisindeki öğelerin sırası kırpma işlemini etkilemez. Dizide belirtilmeyen bir karakter bulunduğunda kırpma durur.  
  
 Aşağıdaki örnek, **TrimEnd** yöntemini kullanarak bir dize son harflerini kaldırır. Bu örnekte, `'r'` dizideki karakterlerin `'W'` sırasının önemli olmadığını göstermek için karakterin ve karakterin konumu tersine çevrilir. Bu kodun ilkinin son `MyString` sözcüğünün artı bir kısmını kaldırdığını unutmayın.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Bu kod `He` konsola görüntülenir.  
  
 Aşağıdaki örnek, **TrimEnd** yöntemini kullanarak bir dize son sözcük kaldırır. Bu kodda virgül sözcüğü `Hello` izler ve virgül kırpılacak karakter dizisinde belirtilmediksin, kırpma virgülle sona erer.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Bu kod `Hello,` konsola görüntülenir.  
  
## <a name="trimstart"></a>TrimStart

 **String.TrimStart** yöntemi, varolan bir dize nesnesinin başlangıcından karakterleri kaldırarak yeni bir dize oluşturması dışında **String.TrimEnd** yöntemine benzer. Kaldırılacak karakterleri belirtmek için **TrimStart** yöntemine bir dizi karakter aktarılır. **TrimEnd** yönteminde olduğu gibi, karakter dizisindeki öğelerin sırası kırpma işlemini etkilemez. Dizide belirtilmeyen bir karakter bulunduğunda kırpma durur.  
  
 Aşağıdaki örnek, bir dize ilk sözcük kaldırır. Bu örnekte, `'l'` dizideki karakterlerin `'H'` sırasının önemli olmadığını göstermek için karakterin ve karakterin konumu tersine çevrilir.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Bu kod `World!` konsola görüntülenir.  
  
## <a name="remove"></a>Kaldır

 Yöntem, <xref:System.String.Remove%2A?displayProperty=nameWithType> varolan bir dizede belirli bir konumda başlayan belirli sayıda karakter kaldırır. Bu yöntem, sıfır tabanlı bir dizin varsayar.  
  
 Aşağıdaki örnek, dize sıfır tabanlı dizinin beşinci konumundan başlayarak bir dizeden on karakter kaldırır.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a>Değiştir

 <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> Ayrıca, yöntemi çağırarak ve yerine boş bir dize (<xref:System.String.Empty?displayProperty=nameWithType>) belirterek, belirli bir karakteri veya alt dizeyi dizeden kaldırabilirsiniz. Aşağıdaki örnek, bir dizedeki tüm virgülleri kaldırır.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
