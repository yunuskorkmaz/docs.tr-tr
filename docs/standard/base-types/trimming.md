---
title: Karakterleri kırpma ve .NET dizelerden kaldırma
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
ms.openlocfilehash: 02704ed5e396e973101bab4e5306d81f5a169d0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Karakterleri kırpma ve .NET dizelerden kaldırma
Tek tek sözcüklere bir cümle ayrıştırma varsa, ya da sözcüğün sonuna boşluk (boşluk olarak da bilinir) sahip sözcükler şunun. Bu durumda, kırpma yöntemlerden birini kullanabilirsiniz **System.String** dizedeki belirtilen alanları veya diğer karakterler herhangi bir sayıda kaldırmak için sınıf. Aşağıdaki tabloda kullanılabilir kırpma yöntemleri açıklar.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Boşluk veya başlangıcını ve bitişini dizenin karakter dizisi belirtilen karakterleri kaldırır.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Bir dize sonu karakter dizisi belirtilen karakterleri kaldırır.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Bir dizenin başından karakter belirtilen karakterleri kaldırır.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Belirtilen dizin konumu bir dizedeki belirtilen sayıda karakteri kaldırır.|  
  
## <a name="trim"></a>Kırpma  
 Kullanarak boşluk her iki ucunu bir dize kolayca kaldırabilirsiniz <xref:System.String.Trim%2A?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi yöntemi.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Başlangıç ve bitiş dizenin karakter dizisinden belirttiğiniz karakter da kaldırabilirsiniz. Aşağıdaki örnek, boşluk karakterleri, nokta ve yıldız kaldırır.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd  
 **String.TrimEnd** yöntemi, yeni bir dize nesnesi oluşturma bir dize sonundan karakterleri kaldırır. Karakter kaldırılacak karakter belirtmek için bu yöntem geçirilir. Karakter dizisindeki öğelerin sırasını kırpma işlemi etkilemez. Dizideki belirtilmemiş bir karakter bulunduğunda kırpma durdurur.  
  
 Aşağıdaki örnek dizesini kullanarak, son harf kaldırır **TrimEnd** yöntemi. Bu örnekte, konumunu `'r'` karakter ve `'W'` karakter tersine dizi karakter sırası önemli değildir olduğunu göstermek için. Bu kodu son sözcüğün kaldırır fark `MyString` ilk parçası artı.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Bu kod görüntüler `He` Konsolu'na.  
  
 Aşağıdaki örnek, bir dizesini kullanarak son word kaldırır **TrimEnd** yöntemi. Bu kodda virgül word izleyen `Hello` ve virgül kırpma karakterleri dizisinde belirtilmediğinden kırpma virgülle biter.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Bu kod görüntüler `Hello,` Konsolu'na.  
  
## <a name="trimstart"></a>TrimStart  
 **String.TrimStart** yöntemi benzer **String.TrimEnd** yöntemi olan dışında var olan bir dize nesnesi baştan karakter kaldırarak yeni bir dize oluşturur. Karakter geçirilir **TrimStart** yöntemi kaldırılacak karakter belirtin. İle **TrimEnd** yöntemi, karakter dizisindeki öğelerin sırasını kırpma işlemi etkilemez. Dizideki belirtilmemiş bir karakter bulunduğunda kırpma durdurur.  
  
 Aşağıdaki örnek, bir dize ilk sözcüğün kaldırır. Bu örnekte, konumunu `'l'` karakter ve `'H'` karakter tersine dizi karakter sırası önemli değildir olduğunu göstermek için.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Bu kod görüntüler `World!` Konsolu'na.  
  
## <a name="remove"></a>Kaldır  
 <xref:System.String.Remove%2A?displayProperty=nameWithType> Yöntemi, belirtilen sayıda varolan bir dizeyi belirtilen konumda başlamak karakteri kaldırır. Bu yöntem, sıfır tabanlı dizin varsayar.  
  
 Aşağıdaki örnek dizenin sıfır tabanlı dizini beş konumunu dize başında on karakterleri kaldırır.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 Ayrıca belirtilen karakter veya alt dize bir dizeden çağırarak kaldırabilirsiniz <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi ve boş bir dize belirtme (<xref:System.String.Empty?displayProperty=nameWithType>) olarak değiştirme. Aşağıdaki örnek, bir dizeden tüm virgül kaldırır.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
