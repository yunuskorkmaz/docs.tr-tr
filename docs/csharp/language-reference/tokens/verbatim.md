---
title: '@- C# Reference'
ms.custom: seodec18
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2290c87f7d4d2ba8da122d4f5ddb9ea423852ec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608726"
---
# <a name="-c-reference"></a>@ (C# Başvuru)

Özel `@` karakter, tam tanımlayıcı işlevi görür. Aşağıdaki yollarla kullanılabilir:

1. Anahtar kelimeleri C# tanımlayıcı olarak kullanılacak şekilde etkinleştirmek için. Karakter, derleyicinin bir C# anahtar sözcük yerine bir tanımlayıcı olarak yorumlanacağı bir kod öğesi ön ekine sahiptir. `@` Aşağıdaki örnek, bir `@` `for` döngüsünde kullandığı adlı `for` bir tanımlayıcıyı tanımlamak için karakterini kullanır.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Dize sabit değerinin tam olarak yorumlandığını göstermek için. Bu `@` örnekteki karakter, tam bir *dize sabit değeri*tanımlar. Basit kaçış dizileri ( `"\\"` ters eğik çizgi gibi), onaltılık kaçış dizileri ( `"\x0041"` büyük a için gibi) ve Unicode kaçış dizileri (örn. bir büyük harf a `"\u0041"` ), tam olarak yorumlanır. Yalnızca bir Quote kaçış sırası (`""`), tam olarak yorumlanmaz; tek tırnak işareti üretir. Bunlara ek olarak, tam olarak bulunan bir [dize](interpolated.md) ayracı kaçış dizileri (`{{` ve `}}`), tam olarak yorumlanmaz; tek küme ayracı karakterleri üretir. Aşağıdaki örnek, biri normal dize değişmez değeri ve diğeri de tam olarak bir dize sabiti kullanarak iki özdeş dosya yolunu tanımlar. Bu, tam dize değişmez değerlerinin yaygın kullanımlarındaki bir biridir.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Aşağıdaki örnek, bir normal dize sabit değeri ve özdeş karakter dizileri içeren tam bir dize sabiti tanımlamanın etkisini gösterir.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Derleyicinin, bir adlandırma çakışması durumunda öznitelikleri birbirinden ayırt etmek üzere etkinleştirmek için. Öznitelik, öğesinden <xref:System.Attribute>türetilen bir sınıftır. Tür adı genellikle sonek **özniteliğini**içerir, ancak derleyici bu kuralı zorlamaz. Daha sonra özniteliğe, tam tür adı (örneğin, `[InfoAttribute]` veya kısaltılmış adı) ile (örneğin, `[Info]`) başvuruda bulunabilir. Ancak, iki kısaltılmış öznitelik türü adı özdeş ise ve bir tür adı **öznitelik** sonekini içeriyorsa ancak diğeri yoksa, bir adlandırma çakışması oluşur. Örneğin, derleyici `Info` veya `InfoAttribute` `Example` özniteliğinin sınıfa uygulanıp uygulanmadığını belirleyemediği için aşağıdaki kod derlenemiyor. Daha fazla bilgi için bkz. [CS1614](../compiler-messages/cs1614.md) .

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Özel Karakterleri](./index.md)
