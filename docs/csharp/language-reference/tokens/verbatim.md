---
title: '@ - C# Referans'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: b37f77273e767a5e5292e7707933892f57811d2a
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291768"
---
# <a name="-c-reference"></a>@ (C# Referans)

Özel `@` karakter, tam anlamıyla tanımlayıcı olarak hizmet vermektedir. Aşağıdaki şekillerde kullanılabilir:

1. C# anahtar kelimelerinin tanımlayıcı olarak kullanılmasını sağlamak için. Karakter, `@` derleyicinin C# anahtar sözcüğü yerine tanımlayıcı olarak yorumlayabilmek için bir kod öğesi önekleri. Aşağıdaki örnek, `@` bir `for` `for` döngüde kullandığı adlı bir tanımlayıcıtanımlamak için karakteri kullanır.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Bir dize harfinin harfi harfine harfiharfini belirtmek için harfi harfi harfine yorumlanmalıdır. Bu `@` örnekteki *karakter, harfi harfine bir dize harfini*tanımlar. Basit kaçış sekansları (ters eğik çizgi gibi), `"\\"` hexadecimal kaçış dizileri (büyük A `"\x0041"` için gibi) ve Unicode kaçış dizileri (a harfi `"\u0041"` için olduğu gibi) kelimenin tam anlamıyla yorumlanır. Sadece bir alıntı`""`kaçış sırası ( ) kelimenin tam anlamıyla yorumlanmaz; bir çift tırnak işareti üretir. Ayrıca, bir kelimenin tam olarak [interpolasyonlu dize](interpolated.md) `{{` ayraç kaçış dizileri durumunda ( ve `}}`) kelimenin tam anlamıyla yorumlanmaz; tek ayraç karakterleri üretirler. Aşağıdaki örnek, biri normal bir dize literal, diğeri ise harfi harfine dize kullanarak iki özdeş dosya yolunu tanımlar. Bu, kelimenin tam anlamıyla dize literals daha yaygın kullanımlarından biridir.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   Aşağıdaki örnekte, normal bir dize edebi ve aynı karakter dizilerini içeren bir harfi harfini tanımlamanın etkisi gösteriş verilmiştir.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Derlemenin bir adlandırma çakışması durumlarında öznitelikleri ayırt etmesini sağlamak için. Öznitelik, <xref:System.Attribute>'den türeyen bir sınıftır. Derleyici bu kuralı zorlamasa da, tür adı genellikle sonek **Özniteliğini**içerir. Öznitelik daha sonra tam tür adı (örneğin, `[InfoAttribute]` ya da kısaltılmış adı (örneğin,) `[Info]`tarafından kod atıfta bulunulabilir. Ancak, iki kısaltılmış öznitelik türü adları aynıysa ve bir tür adı **Atöz** soneki içeriyorsa, ancak diğerinde yoksa bir adlandırma çakışması oluşur. Örneğin, derleyici `Info` `InfoAttribute` `Example` sınıfa mı yoksa öznitelik mi uygulandığını belirleyemediğinden aşağıdaki kod derlenemez. Daha fazla bilgi için [CS1614'e](../compiler-messages/cs1614.md) bakın.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Özel Karakterleri](./index.md)
