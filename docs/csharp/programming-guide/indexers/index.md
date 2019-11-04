---
title: Dizin oluşturucular C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 02dc8c21b86438c801fb151d9f02a223b60d6197
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423230"
---
# <a name="indexers-c-programming-guide"></a>Dizin Oluşturucular (C# Programlama Kılavuzu)

Dizin oluşturucular, bir sınıf veya yapının örneklerinin, tıpkı diziler gibi dizine eklenmesine izin verir. Dizinli değer, açıkça bir tür veya örnek üyesi belirtilmeden ayarlanabilir veya alınabilir. Dizin oluşturucular, erişimcilerinin parametre kazanması dışında [özelliklere](../classes-and-structs/properties.md) benzer.  

 Aşağıdaki örnek, değer atamak ve almak için basit [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) erişimcisi yöntemleriyle genel bir sınıf tanımlar. `Program` sınıfı dizeleri depolamak için bu sınıfın bir örneğini oluşturur.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> Daha fazla örnek için bkz. [Ilgili bölümler](./index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  
 
Bir dizin oluşturucunun Get veya set erişimcisinin bir değer döndüren ya da ayarlayan tek bir deyimden oluşması yaygındır. İfade-Bodied Üyeler, bu senaryoyu desteklemek için basitleştirilmiş bir sözdizimi sağlar. C# 6 ' dan itibaren, aşağıdaki örnekte gösterildiği gibi, salt okunurdur bir Dizin Oluşturucu, bir ifade Bodied üyesi olarak uygulanabilir.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

`=>` ifade gövdesini tanıtdığına ve `get` anahtar sözcüğünün kullanılmadığını unutmayın. 

7,0 ile C# başlayarak, hem Get hem de set erişimcisi, ifade Bodied Üyeler olarak uygulanan bir uygulanmış olabilir. Bu durumda, hem `get` hem de `set` anahtar sözcükleri kullanılmalıdır. Örneğin:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Dizin Oluşturuculara Genel Bakış  
  
- Dizin oluşturucular, nesnelerin dizilere benzer bir şekilde dizine alınmasını sağlar.  
  
- `get` erişimcisi bir değer döndürür. `set` erişimcisi bir değer atar.  
  
- [Bu](../../language-reference/keywords/this.md) anahtar sözcük, Dizin oluşturucuyu tanımlamak için kullanılır.  
  
- [Value](../../language-reference/keywords/value.md) anahtar sözcüğü, `set` Indexer tarafından atanan değeri tanımlamak için kullanılır.  
  
- Dizin oluşturucuların bir tamsayı değeri ile dizinlenmesini gerekmez; Bu, belirli bir arama mekanizmasını nasıl tanımlayacaksınız.  
  
- Dizin oluşturucular aşırı yüklenebilir.  
  
- Dizin oluşturucular birden fazla biçimsel parametreye sahip olabilir, örneğin iki boyutlu bir diziye erişirken.  
  
## <a name="BKMK_RelatedSections"></a>İlgili bölümler  
  
- [Dizin Oluşturucular Kullanma](./using-indexers.md)  
  
- [Arabirimlerdeki Dizin Oluşturucular](./indexers-in-interfaces.md)  
  
- [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](./comparison-between-properties-and-indexers.md)  
  
- [Erişimci Erişilebilirliğini Kısıtlama](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Dizin oluşturucular](~/_csharplang/spec/classes.md#indexers) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Veri Erişimi](../classes-and-structs/properties.md)
