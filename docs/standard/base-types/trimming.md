---
title: .NET 'teki Dizelerdeki karakterleri kırpma ve kaldırma
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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159994"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>.NET 'teki Dizelerdeki karakterleri kırpma ve kaldırma
Bir tümceyi tek tek sözcüklere ayrıştırdıysanız, sözcüğün her iki ucunda da boşluk olan (boşluk da denir) sözcüklerden oluşan sözcüklerle karşılaşabilirsiniz. Bu durumda, dizedeki belirli bir konumdan herhangi bir sayıda boşluğu veya diğer karakteri kaldırmak için **System. String** sınıfındaki trim yöntemlerinden birini kullanabilirsiniz. Aşağıdaki tabloda kullanılabilir kırpma yöntemleri açıklanmaktadır.  
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Bir dizenin başındaki ve sonundaki karakter dizisinde belirtilen boşluk veya karakterleri kaldırır.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Bir dizenin sonundaki karakter dizisinde belirtilen karakterleri kaldırır.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Bir karakter dizisinde belirtilen karakterleri dizenin başından kaldırır.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Bir dizedeki belirtilen dizin konumundan belirtilen sayıda karakteri kaldırır.|  
  
## <a name="trim"></a>kırpma

 Aşağıdaki örnekte gösterildiği gibi, <xref:System.String.Trim%2A?displayProperty=nameWithType> yöntemini kullanarak, bir dizenin her iki ucunda da kolayca beyaz boşluk çıkarabilirsiniz.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Bir dizenin başındaki ve sonundaki bir karakter dizisinde belirttiğiniz karakterleri de kaldırabilirsiniz. Aşağıdaki örnek boşluk karakterlerini, dönemleri ve yıldız işaretlerini kaldırır.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd

 **String. TrimEnd** yöntemi bir dizenin sonundaki karakterleri kaldırır ve yeni bir dize nesnesi oluşturur. Kaldırılacak karakterleri belirtmek için bu yönteme bir karakter dizisi geçirilir. Karakter dizisindeki öğelerin sırası, kırpma işlemini etkilemez. Dizide belirtilen bir karakter bulunduğunda kırpma durdu.  
  
 Aşağıdaki örnek, **TrimEnd** yöntemini kullanarak bir dizenin son harflerini kaldırır. Bu örnekte, dizideki karakterlerin sırasının ne olduğunu göstermek için `'r'` karakterinin ve `'W'` karakterin konumu tersine çevrilir. Bu kodun `MyString` son sözcüğünü ve ilk öğesinin bir kısmını kaldırdığına dikkat edin.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Bu kod konsola `He` görüntüler.  
  
 Aşağıdaki örnek, **TrimEnd** yöntemini kullanarak bir dizenin son sözcüğünü kaldırır. Bu kodda, bir virgül `Hello` kelimedir ve bu sayı kırpılacak karakter dizisinde, kırpma, virgülden sona erer.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Bu kod konsola `Hello,` görüntüler.  
  
## <a name="trimstart"></a>TrimStart

 **String. Kırosstart** yöntemi **String. TrimEnd** yöntemine benzer, ancak karakterleri varolan bir dize nesnesinin başından kaldırarak yeni bir dize oluşturur. Kaldırılacak karakterleri belirtmek için, bir karakter dizisi **kırılımı başlangıç** yöntemine geçirilir. **TrimEnd** yönteminde olduğu gibi, karakter dizisindeki öğelerin sırası trim işlemini etkilemez. Dizide belirtilen bir karakter bulunduğunda kırpma durdu.  
  
 Aşağıdaki örnek bir dizenin ilk sözcüğünü kaldırır. Bu örnekte, dizideki karakterlerin sırasının ne olduğunu göstermek için `'l'` karakterinin ve `'H'` karakterin konumu tersine çevrilir.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Bu kod konsola `World!` görüntüler.  
  
## <a name="remove"></a>Kaldır

 <xref:System.String.Remove%2A?displayProperty=nameWithType> yöntemi, varolan bir dizedeki belirli bir konumda başlayan belirtilen sayıda karakteri kaldırır. Bu yöntem sıfır tabanlı bir dizini varsayar.  
  
 Aşağıdaki örnek, dizenin sıfır tabanlı dizininin beş konumunda başlayan bir dizeden on karakteri kaldırır.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a>Değiştir

 Ayrıca, <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemini çağırarak ve değiştirme olarak boş bir dize (<xref:System.String.Empty?displayProperty=nameWithType>) belirterek, bir dizeden belirtilen bir karakteri veya alt dizeyi kaldırabilirsiniz. Aşağıdaki örnek bir dizeden tüm virgülleri kaldırır.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
