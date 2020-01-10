---
title: C# başvuru al
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: d6c0452a7890a6ade480054115c1383199a3f91c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713500"
---
# <a name="get-c-reference"></a>get (C# Başvurusu)

`get` anahtar sözcüğü, özellik değeri veya Indexer öğesi döndüren bir özellikte veya dizin oluşturucuda bir *erişimci* yöntemi tanımlar. Daha fazla bilgi için bkz. [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Otomatik uygulanan özellikler](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ve [Dizin oluşturucular](../../programming-guide/indexers/index.md).  
  
Aşağıdaki örnek, `Seconds`adlı bir özellik için hem `get` hem de `set` erişimcisi tanımlar. Özellik değerini geri yüklemek için `_seconds` adlı bir özel alan kullanır.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Genellikle `get` erişimcisi, önceki örnekte olduğu gibi bir değer döndüren tek bir deyimden oluşur. 7,0 ' C# den başlayarak, `get` erişimcisini ifade-Bodied üyesi olarak uygulayabilirsiniz. Aşağıdaki örnek, ifadesi Bodied Üyeler olarak hem `get` hem de `set` erişimcisini uygular.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
Bir özelliğin `get` ve `set` erişimcilerinin özel bir destek alanındaki bir değeri ayarlamaktan veya almadan başka bir işlem gerçekleştirmesinin gerçekleştirdiği basit durumlar için C# derleyicinin otomatik uygulanan özellikler desteğiyle yararlanabilirsiniz. Aşağıdaki örnek, `Hours` otomatik olarak uygulanan bir özellik olarak uygular. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [Veri Erişimi](../../programming-guide/classes-and-structs/properties.md)
