---
title: "Numaralandırma Biçimi Dizeleri"
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
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0992d8591711073f9094c29fad980a8e652e686
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="enumeration-format-strings"></a>Numaralandırma Biçimi Dizeleri
Kullanabileceğiniz <xref:System.Enum.ToString%2A?displayProperty=nameWithType> sayısal, onaltılık veya bir numaralandırma üyesine dize değerini temsil eden yeni bir dize nesnesi oluşturmak için yöntemi. Bu yöntem biçimlendirme döndürmesini istediğiniz değeri belirtmek için dizeleri numaralandırması birini alır.  
  
 Biçimlendirme dizeleri ve bunların dönüş değerleri numaralandırma aşağıdaki tabloda listelenmektedir. Bu biçim belirticileri büyük küçük harfe duyarlı değildir.  
  
| Biçim dizesi | Sonuç |  
| ------------- | ------ |  
| G veya g | Numaralandırma Giriş bir dize değeri, mümkünse ve aksi takdirde geçerli örneğinin tamsayı değeri görüntüler. Numaralandırma ile tanımlanmış olması durumunda **bayrakları** öznitelik kümesi, her geçerli giriş değerleri birleştirilmiş birlikte dize virgülle ayrılmış. Varsa **bayrakları** özniteliği ayarlanmamışsa, geçersiz bir değer sayısal girişi olarak görüntülenir. Aşağıdaki örnek G biçim belirticisi gösterilmektedir.<br><br>[!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)] |  
| F veya f | Numaralandırma giriş mümkünse bir dize değeri olarak görüntüler. Değeri, listedeki girişleri toplamı olarak tamamen görüntülenebilir varsa (olsa bile **bayrakları** özniteliği mevcut değil), virgülle ayrılmış geçerli her girişin dize değerlerini birlikte birleşir. Değer tamamen numaralandırması girdileri tarafından belirlenemiyorsa değeri tamsayı biçimlendirilir. Aşağıdaki örnek F biçim belirticisi gösterilmektedir.<br><br>[!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)] |  
| D veya d | Olası en kısa gösteriminde bir tamsayı değeri olarak numaralandırma giriş görüntüler. Aşağıdaki örnek, D biçim belirticisi gösterilmektedir.<br><br>[!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)] |  
| X veya x | Numaralandırma girişi bir onaltılık değer olarak görüntüler. Değeri, değerin en az sekiz basamak uzunluğunda olduğundan emin olmak için gerektiği gibi sıfırları ile gösterilir. Aşağıdaki örnek X biçim belirticisi gösterilmektedir.<br /><br /> [!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)] |  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek olarak adlandırılan bir numaralandırma tanımlar `Colors` üç girişlerinin oluşur: `Red`, `Blue`, ve `Green`.  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 Numaralandırma tanımlandıktan sonra aşağıdaki biçimde bir örneği bildirilebilir.  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 `Color.ToString(System.String)` Yöntemi sonra kendisine geçirilen biçim belirticisi bağlı olarak, farklı şekillerde numaralandırma değeri görüntülemek için kullanılabilir.  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirme türleri](../../../docs/standard/base-types/formatting-types.md)
