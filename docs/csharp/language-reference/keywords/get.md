---
description: Get-C# başvurusu
title: Get-C# başvurusu
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 7e13dc3ed6577717c64b4e36000a9e090f7b4751
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139742"
---
# <a name="get-c-reference"></a>get (C# Başvurusu)

`get`Anahtar sözcüğü, özellik değeri veya Indexer öğesi döndüren bir özellikte veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar. Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).  
  
Aşağıdaki örnek `get` `set` adlı bir özellik için hem hem de erişimcisini tanımlar `Seconds` . `_seconds`Özellik değerini geri yüklemek için adlı bir özel alan kullanır.  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Genellikle, `get` erişimci, önceki örnekte olduğu gibi bir değer döndüren tek bir deyimden oluşur. C# 7,0 ' den başlayarak, `get` erişimciyi bir ifade olarak uygulayabilirsiniz. Aşağıdaki örnek, hem hem de `get` `set` erişimcisini ifade-Bodied Üyeler olarak uygular.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirdiği basit durumlarda, C# derleyicisinin otomatik uygulanan özellikler için destek özelliğinden yararlanabilirsiniz. Aşağıdaki örnek `Hours` Otomatik uygulanan bir özellik olarak uygulanır.
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](./index.md)
- [Özellikler](../../programming-guide/classes-and-structs/properties.md)
