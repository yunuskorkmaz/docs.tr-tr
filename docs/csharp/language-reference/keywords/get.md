---
title: get - C# Referans
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 61d8c02aaf13f43ff8ea17c1e868ea9fd52893c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173633"
---
# <a name="get-c-reference"></a>get (C# Başvurusu)

Anahtar `get` kelime, özellik değerini veya dizinleyici öğesini döndüren bir özellik veya dizinleyicide bir *erişimci* yöntemi tanımlar. Daha fazla bilgi için bkz: [Özellikler,](../../programming-guide/classes-and-structs/properties.md) [Otomatik Uygulanan Özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ve [Dizinleyiciler.](../../programming-guide/indexers/index.md)  
  
Aşağıdaki örnek, adlandırılmış `get` `Seconds`bir `set` özellik için hem a hem de bir erişimci tanımlar. Özellik değerini yedeklemek `_seconds` için özel bir alan kullanır.  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Genellikle, `get` erişimci önceki örnekte olduğu gibi bir değer döndüren tek bir deyimoluşur. C# 7.0 ile başlayarak, `get` erişime gireni ifade gövdeli bir üye olarak uygulayabilirsiniz. Aşağıdaki örnek, hem `get` erişime `set` gireni hem de katılımcıyı ifade gövdeli üyeler olarak uygular.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

Bir özelliğin `get` ve `set` erişime sahip olanların özel bir destek alanında bir değer ayarlamaktan veya almaktan başka bir işlem gerçekleştirmediği basit durumlarda, Otomatik olarak uygulanan özellikler için C# derleyicisinin desteğinden yararlanabilirsiniz. Aşağıdaki örnek, `Hours` otomatik olarak uygulanan bir özellik olarak uygular.
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Özellikler](../../programming-guide/classes-and-structs/properties.md)
