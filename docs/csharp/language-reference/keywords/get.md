---
title: C# başvuru al
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 783814a575e95fc9deb5c9cdef235a5636f5f529
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602138"
---
# <a name="get-c-reference"></a>get (C# Başvurusu)

Anahtar sözcüğü, özellik değeri veya Indexer öğesi döndüren bir özellikte veya dizin oluşturucuda bir erişimci yöntemi tanımlar. `get` Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).  
  
Aşağıdaki örnek adlı `get` `set` birözellik`Seconds`için hem hem de erişimcisini tanımlar. Özellik değerini geri yüklemek için adlı `_seconds` bir özel alan kullanır.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Genellikle, `get` erişimci, önceki örnekte olduğu gibi bir değer döndüren tek bir deyimden oluşur. 7,0 ' C# den başlayarak, `get` erişimciyi bir ifade olarak uygulayabilirsiniz. Aşağıdaki örnek, `get` `set` hem hem de erişimcisini ifade-Bodied Üyeler olarak uygular.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirdiği basit durumlarda, C# derleyicinin otomatik olarak uygulanmış olan desteğiyle faydalanabilirsiniz özelliklerinin. Aşağıdaki örnek `Hours` otomatik uygulanan bir özellik olarak uygulanır. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Özellikler](../../programming-guide/classes-and-structs/properties.md)
