---
title: '@- C# Reference'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: a3446eceb0d3c415e36ea1d2c7d8d6d34f65350d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712422"
---
# <a name="-c-reference"></a>@ (C# Başvuru)

`@` özel karakter, tam tanımlayıcı işlevi görür. Aşağıdaki yollarla kullanılabilir:

1. Anahtar kelimeleri C# tanımlayıcı olarak kullanılacak şekilde etkinleştirmek için. `@` karakter, derleyicinin bir C# anahtar sözcük yerine bir tanımlayıcı olarak yorumlanacağı bir kod öğesi ön ekine sahiptir. Aşağıdaki örnek, bir `for` döngüsünde kullandığı `for` adlı bir tanımlayıcıyı tanımlamak için `@` karakterini kullanır.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Dize sabit değerinin tam olarak yorumlandığını göstermek için. Bu örnekteki `@` karakteri, tam bir *dize sabit değeri*tanımlar. Basit kaçış dizileri (ters eğik çizgi için `"\\"` gibi), onaltılık kaçış dizileri (büyük A için `"\x0041"` gibi) ve Unicode kaçış dizileri (örn. bir büyük harf A için `"\u0041"`), tam olarak yorumlanır. Yalnızca bir tırnak çıkış sırası (`""`), salt okunur olarak yorumlanmaz; tek tırnak işareti üretir. Ayrıca, tam olarak bulunan bir [dize](interpolated.md) ayracı kaçış dizileri (`{{` ve `}}`) büyük harf olarak yorumlanmaz; tek küme ayracı karakterleri üretir. Aşağıdaki örnek, biri normal dize değişmez değeri ve diğeri de tam olarak bir dize sabiti kullanarak iki özdeş dosya yolunu tanımlar. Bu, tam dize değişmez değerlerinin yaygın kullanımlarındaki bir biridir.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Aşağıdaki örnek, bir normal dize sabit değeri ve özdeş karakter dizileri içeren tam bir dize sabiti tanımlamanın etkisini gösterir.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Derleyicinin, bir adlandırma çakışması durumunda öznitelikleri birbirinden ayırt etmek üzere etkinleştirmek için. Öznitelik, <xref:System.Attribute>türetilen bir sınıftır. Tür adı genellikle sonek **özniteliğini**içerir, ancak derleyici bu kuralı zorlamaz. Daha sonra bu özniteliğe, tam tür adı (örneğin, `[InfoAttribute]` veya kısaltılmış adı (örneğin, `[Info]`) ile kod içinde başvurulabilir. Ancak, iki kısaltılmış öznitelik türü adı özdeş ise ve bir tür adı **öznitelik** sonekini içeriyorsa ancak diğeri yoksa, bir adlandırma çakışması oluşur. Örneğin, derleyici `Info` veya `InfoAttribute` özniteliğinin `Example` sınıfına uygulanıp uygulanmadığını belirleyemediği için aşağıdaki kod derlenemiyor. Daha fazla bilgi için bkz. [CS1614](../compiler-messages/cs1614.md) .

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Özel Karakterleri](./index.md)
