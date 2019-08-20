---
title: Diziler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 24c6d54c3fe92ada661e732adec582e87ab62417
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597523"
---
# <a name="arrays-c-programming-guide"></a>Diziler (C# Programlama Kılavuzu)

Aynı türde birden çok değişkeni bir dizi veri yapısına saklayabilirsiniz. Öğelerinin türünü belirterek bir dizi bildirirsiniz.  
  
 `type[] arrayName;`  
  
 Aşağıdaki örnek, tek boyutlu, çok boyutlu ve pürüzlü Diziler oluşturur:  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a>Diziye genel bakış

 Bir dizi aşağıdaki özelliklere sahiptir:  
  
- Bir dizi [tek boyutlu](./single-dimensional-arrays.md), [çok boyutlu](./multidimensional-arrays.md) veya [pürüzlü](./jagged-arrays.md)olabilir.  
  
- Boyut sayısı ve her boyutun uzunluğu, dizi örneği oluşturulduğunda oluşturulur. Bu değerler, örneğin kullanım ömrü boyunca değiştirilemez.  
  
- Sayısal dizi öğelerinin varsayılan değerleri sıfır olarak ayarlanır ve başvuru öğeleri null olarak ayarlanır.  
  
- Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve olarak `null`başlatılır.  
  
- Diziler sıfır dizinli: öğeleri olan `n` bir dizi ' `n-1`dan `0` ' a dizinlenir.  
  
- Dizi öğeleri, bir dizi türü de dahil olmak üzere herhangi bir türde olabilir.  
  
- Dizi türleri, soyut temel türden <xref:System.Array>türetilmiş [başvuru türleridir](../../language-reference/keywords/reference-types.md) . Bu tür ve <xref:System.Collections.Generic.IEnumerable%601>uyguladığından <xref:System.Collections.IEnumerable> , içindeki C#tüm dizilerde [foreach](../../language-reference/keywords/foreach-in.md) yineleme kullanabilirsiniz.  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
- [Nesne Olarak Diziler](./arrays-as-objects.md)  
  
- [Dizilerle foreach kullanma](./using-foreach-with-arrays.md)  
  
- [Dizileri Bağımsız Değişkenler Olarak Geçirme](./passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Koleksiyonlar](../concepts/collections.md)
