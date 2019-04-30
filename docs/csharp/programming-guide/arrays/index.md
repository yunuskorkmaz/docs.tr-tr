---
title: Diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 1b1a3d2e61507a497349deeb857e4333356f66a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61684022"
---
# <a name="arrays-c-programming-guide"></a>Diziler (C# Programlama Kılavuzu)

Bir dizi veri yapısında aynı türde birden fazla değişken depolayabilirsiniz. Bir diziyi, öğelerinin türünü belirterek bildirin.  
  
 `type[] arrayName;`  
  
 Aşağıdaki örnek, tek boyutlu, çok boyutlu ve düzensiz diziler oluşturur:  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a>Diziye genel bakış

 Bir dizi aşağıdaki özelliklere sahiptir:  
  
- Bir dizi olabilir [tek boyutlu](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [çok boyutlu](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) veya [düzensiz](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
- Boyutların sayısı ve her boyutun uzunluğu, dizi örneği oluşturulduğunda oluşturulur. Bu değerler örneğin kullanım süresi boyunca değiştirilemez.  
  
- Sayısal dizi öğelerinin varsayılan değerleri sıfır olarak ayarlanır ve başvuru öğeleri ayarlanmış null.  
  
- Düzensiz bir dizi, dizilerin bir dizidir ve bu nedenle öğeleri başvuru türleridir ve başlatılır `null`.  
  
- Diziler sıfır dizinlidir şunlardır: bir diziyi `n` öğeleri arasında dizinlenir `0` için `n-1`.  
  
- Dizi öğeleri, bir dizi türü de dahil olmak üzere, herhangi bir türde olabilir.  
  
- Dizi türleri, [başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md) soyut temel türünden türetilmiş <xref:System.Array>. Bu tür uyguladığından <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601>, kullanabileceğiniz [foreach](../../../csharp/language-reference/keywords/foreach-in.md) C# içindeki dizilerde yineleme.  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
- [Nesne Olarak Diziler](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
- [Dizilerle foreach kullanma](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
- [Dizileri Bağımsız Değişkenler Olarak Geçirme](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Koleksiyonlar](../../../csharp/programming-guide/concepts/collections.md)
