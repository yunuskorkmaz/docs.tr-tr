---
description: '@-C# başvurusu'
title: '@-C# başvurusu'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: 7d78b28479ed6128321207073dc94976710f10b6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138910"
---
# <a name="-c-reference"></a>@ (C# Başvurusu)

`@`Özel karakter, tam tanımlayıcı işlevi görür. Aşağıdaki yollarla kullanılabilir:

1. C# anahtar sözcüklerini tanımlayıcı olarak kullanılacak şekilde etkinleştirmek için. `@`Karakter, derleyicinin bir C# anahtar sözcüğü yerine bir tanımlayıcı olarak yorumlanacağı bir kod öğesi ön ekine sahiptir. Aşağıdaki örnek, `@` bir döngüsünde kullandığı adlı bir tanımlayıcıyı tanımlamak için karakterini kullanır `for` `for` .

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Dize sabit değerinin tam olarak yorumlandığını göstermek için. `@`Bu örnekteki karakter, tam bir *dize sabit değeri*tanımlar. Basit kaçış dizileri ( `"\\"` ters eğik çizgi gibi), onaltılık kaçış dizileri ( `"\x0041"` büyük a için gibi) ve Unicode kaçış dizileri (örn `"\u0041"` . bir büyük harf a), tam olarak yorumlanır. Yalnızca bir Quote kaçış sırası ( `""` ), tam olarak yorumlanmaz; bir çift tırnak işareti üretir. Bunlara ek olarak, tam olarak bulunan bir [dize](interpolated.md) ayracı kaçış dizileri ( `{{` ve), tam olarak `}}` yorumlanmaz; tek küme ayracı karakterleri üretir. Aşağıdaki örnek, biri normal dize değişmez değeri ve diğeri de tam olarak bir dize sabiti kullanarak iki özdeş dosya yolunu tanımlar. Bu, tam dize değişmez değerlerinin yaygın kullanımlarındaki bir biridir.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Aşağıdaki örnek, bir normal dize sabit değeri ve özdeş karakter dizileri içeren tam bir dize sabiti tanımlamanın etkisini gösterir.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Derleyicinin, bir adlandırma çakışması durumunda öznitelikleri birbirinden ayırt etmek üzere etkinleştirmek için. Öznitelik, öğesinden türetilen bir sınıftır <xref:System.Attribute> . Tür adı genellikle sonek **özniteliğini**içerir, ancak derleyici bu kuralı zorlamaz. Daha sonra özniteliğe, tam tür adı (örneğin, `[InfoAttribute]` veya kısaltılmış adı) ile (örneğin,) başvuruda bulunabilir `[Info]` . Ancak, iki kısaltılmış öznitelik türü adı özdeş ise ve bir tür adı **öznitelik** sonekini içeriyorsa ancak diğeri yoksa, bir adlandırma çakışması oluşur. Örneğin, derleyici `Info` veya `InfoAttribute` özniteliğinin sınıfa uygulanıp uygulanmadığını belirleyemediği için aşağıdaki kod derlenemiyor `Example` . Daha fazla bilgi için bkz. [CS1614](../compiler-messages/cs1614.md) .

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# özel karakterleri](./index.md)
