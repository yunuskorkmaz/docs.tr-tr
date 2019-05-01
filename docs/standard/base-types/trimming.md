---
title: Karakterleri kırpma ve. NET'te dizelerden kaldırma
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d13d4e115caa636e5d760b65bc98e195490f911
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965171"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Karakterleri kırpma ve. NET'te dizelerden kaldırma
Kelimeler bir cümle ayrıştırma ise, word'ün her iki ucunda boşluk (boşluk olarak da bilinir) sahip sözcük çıkabilir. Bu durumda, kırpma metotlarından birini kullanabilirsiniz **System.String** dizedeki belirtilen herhangi bir sayıda boşluk veya diğer karakterler kaldırmak için sınıf. Aşağıdaki tabloda kullanılabilir kesim yöntemleri açıklar.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Boşluk veya bir dizenin sonunda ve başındaki karakter dizisi içinde belirtilen karakterleri kaldırır.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Bir dizenin sonuna karakterler dizisi belirtilen karakterleri kaldırır.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Bir dize başından itibaren karakter belirtilen karakterleri kaldırır.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Bir dizedeki bir belirtilen dizine belirtilen sayıda karakteri kaldırır.|  
  
## <a name="trim"></a>Kırpma  
 Kullanarak boşluk her iki ucunda da bir dize kolayca kaldırabilirsiniz <xref:System.String.Trim%2A?displayProperty=nameWithType> yöntemi, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Ayrıca, bir karakter dizisinden bir dizenin sonunda ve başındaki belirttiğiniz karakter kaldırabilirsiniz. Aşağıdaki örnek, boşluk karakteri, nokta ve yıldız kaldırır.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd  
 **String.TrimEnd** yöntemi yeni bir dize nesnesi oluşturma, bir dizenin sonundan karakterleri kaldırır. Bir karakter dizisini kaldırılacak karakter belirtmek için bu yönteme geçirilir. Karakter dizisinde öğelerin sırasını kesme işlemi etkilemez. Trim dizide belirtilmemiş bir karakter bulunduğunda durur.  
  
 Aşağıdaki örnek, bir dize kullanarak, son harf kaldırır **TrimEnd** yöntemi. Bu örnekte, konumunu `'r'` karakter ve `'W'` karakteri ters dizideki karakterlerin sırası önemli değildir göstermek için. Bu kod, son sözcüğü kaldırır fark `MyString` artı ilk parçası.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Bu kod görüntüler `He` konsola.  
  
 Aşağıdaki örneği kullanarak bir dize olan son sözcüğü kaldırır **TrimEnd** yöntemi. Bu kodda virgül sözcüğünü izleyen `Hello` ve virgül içerecek şekilde kırpmanıza karakter dizisinde belirtilmediğinden, kırpma virgülle biter.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Bu kod görüntüler `Hello,` konsola.  
  
## <a name="trimstart"></a>TrimStart  
 **String.TrimStart** yöntemi benzer **String.TrimEnd** yöntemi dışında olan mevcut bir dize nesnesi başından itibaren karakter kaldırarak yeni bir dize oluşturur. Karakter dizisi geçirilir **TrimStart** kaldırılacak karakter belirtmek için yöntemi. Olduğu gibi **TrimEnd** yöntemi, karakter dizideki öğelerin sırasını kesme işlemi etkilemez. Trim dizide belirtilmemiş bir karakter bulunduğunda durur.  
  
 Aşağıdaki örnek bir dizenin ilk sözcük kaldırır. Bu örnekte, konumunu `'l'` karakter ve `'H'` karakteri ters dizideki karakterlerin sırası önemli değildir göstermek için.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Bu kod görüntüler `World!` konsola.  
  
## <a name="remove"></a>Kaldır  
 <xref:System.String.Remove%2A?displayProperty=nameWithType> Yöntemi, belirtilen sayıda varolan bir dizeyi, belirtilen konumda başlayan karakteri kaldırır. Bu yöntem, sıfır tabanlı dizin varsayar.  
  
 Aşağıdaki örnek, dizenin bir sıfır tabanlı dizini beş konumunda başlayan bir dizedeki on karakterlerini kaldırır.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 Ayrıca belirtilen karakter veya alt dizenin bir dizeden çağırarak kaldırabilirsiniz <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi ve boş bir dize belirtme (<xref:System.String.Empty?displayProperty=nameWithType>) yerine. Aşağıdaki örnek, bir dizedeki tüm virgül kaldırır.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
