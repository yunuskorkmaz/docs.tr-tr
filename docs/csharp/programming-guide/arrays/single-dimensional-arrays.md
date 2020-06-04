---
title: Tek boyutlu diziler-C# Programlama Kılavuzu
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: e189253eedc21fa2d51e16407f04b034610bb57b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410250"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tek Boyutlu Diziler (C# Programlama Kılavuzu)

Dizi öğesi türünü ve öğe sayısını belirten [New](../../language-reference/operators/new-operator.md) işlecini kullanarak tek boyutlu bir dizi oluşturursunuz. Aşağıdaki örnek, beş tamsayının dizisini bildirir:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

Bu dizi öğesine öğesinden öğelerini içerir `array[0]` `array[4]` . Dizi öğeleri, tamsayılar için, öğe türünün varsayılan değerine başlatılır `0` .

Diziler, bir dizi dizeyi bildiren aşağıdaki örnek gibi, belirttiğiniz herhangi bir öğe türünü depolayabilirler:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a>Dizi başlatma

Diziyi bildirdiğinizde dizideki öğeleri başlatabilirsiniz. Başlangıç listesindeki öğe sayısı tarafından çıkarsandığı için uzunluk belirleyicisi gerekli değildir. Örnek:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

Aşağıdaki kod, her dizi öğesinin bir günün adı ile başlatıldığı dize dizisinin bir bildirimini gösterir:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
`new`Aşağıdaki kodda gösterildiği gibi, bildirim üzerine bir diziyi başlattığınızda ifadeden ve dizi türünden kaçınabilirsiniz. Buna [örtük olarak yazılmış dizi](implicitly-typed-arrays.md)denir:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

Bir dizi değişkenini oluşturmadan bildirebilirsiniz, ancak `new` Bu değişkene yeni bir dizi atadığınızda işlecini kullanmanız gerekir. Örnek:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a>Değer türü ve başvuru türü dizileri

Aşağıdaki dizi bildirimini göz önünde bulundurun:  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

Bu deyimin sonucu, `SomeType` bir değer türü veya başvuru türü olmasına bağlıdır. Değer bir tür ise, ifade, her birinin türü olan 10 öğeden oluşan bir dizi oluşturur `SomeType` . `SomeType`Bir başvuru türü ise, ifade her biri null başvuruya başlatılan 10 öğeden oluşan bir dizi oluşturur. Her iki örnekte de öğeler, öğe türü için varsayılan değer olarak başlatılır. Değer türleri ve başvuru türleri hakkında daha fazla bilgi için bkz. [değer türleri](../../language-reference/builtin-types/value-types.md) ve [başvuru türleri](../../language-reference/keywords/reference-types.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [Diziler](./index.md)
- [Çok Boyutlu Diziler](./multidimensional-arrays.md)
- [Düzensiz Diziler](./jagged-arrays.md)
