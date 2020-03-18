---
title: Dizinleyiciler - C# Programlama Kılavuzu
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 539b2861e975c0c758c43c8a5d4cca86e3d2bb2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167550"
---
# <a name="indexers-c-programming-guide"></a>Dizin Oluşturucular (C# Programlama Kılavuzu)

Dizin leyiciler, bir sınıf veya yapı örneklerinin diziler gibi diziler gibi diziler gibi dizilere eksitre ekilmesine izin verir. Dizinlenen değer, bir tür veya örnek üye açıkça belirtilmeden ayarlanabilir veya alınabilir. Dizinleyiciler, erişimcilerin parametreleri alması dışında [özelliklere](../classes-and-structs/properties.md) benzer.  

 Aşağıdaki örnek, değerleri atamak ve almak için basit [get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) erişimci yöntemleri ile genel bir sınıf tanımlar. Sınıf `Program` dizeleri depolamak için bu sınıfın bir örneği oluşturur.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> Daha fazla örnek [için, İlgili Bölümlere](./index.md#BKMK_RelatedSections)bakın.  
  
## <a name="expression-body-definitions"></a>İfade Gövde Tanımları  

Bir dizin leyicinin erişime sahip olması veya ayarlayan bir değeri döndüren veya ayarlayan tek bir deyimden oluşması yaygındır. İfade gövdeli üyeler, bu senaryoyu desteklemek için basitleştirilmiş bir sözdizimi sağlar. C# 6 ile başlayarak, aşağıdaki örnekte görüldüğü gibi, salt okunur dizinleyici ifade gövdeli bir üye olarak uygulanabilir.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

İfade `=>` gövdesini tanıttıve anahtar kelimenin `get` kullanılmadığını unutmayın.

C# 7.0 ile başlayarak, hem get hem de set erişimcisi ifade gövdeli üyeler olarak uygulanabilir. Bu durumda, `get` hem `set` anahtar kelimeler hem de anahtar kelimeler kullanılmalıdır. Örnek:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Dizin Oluşturuculara Genel Bakış  
  
- Dizin leyiciler nesnelerin dizilere benzer şekilde dizilmesini sağlar.  
  
- Bir `get` erişimci bir değer döndürür. Bir `set` erişimci bir değer atar.  
  
- [Bu](../../language-reference/keywords/this.md) anahtar kelime dizinleyicitanımlamak için kullanılır.  
  
- [Değer](../../language-reference/keywords/value.md) anahtar kelimesi `set` dizinleyici tarafından atanan değeri tanımlamak için kullanılır.  
  
- Dizinleyicilerin bir sonda değeriyle dizine eklenmeleri gerekmez; belirli bir arama mekanizmasını nasıl tanımlayacak size kalmış.  
  
- Dizin leyiciler aşırı yüklenebilir.  
  
- Dizin leyicilerin, örneğin iki boyutlu bir diziye erişirken birden fazla resmi parametresi olabilir.  
  
## <a name="BKMK_RelatedSections"></a>İlgili Bölümler  
  
- [Dizin Oluşturucular Kullanma](./using-indexers.md)  
  
- [Arabirimlerdeki Dizin Oluşturucular](./indexers-in-interfaces.md)  
  
- [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](./comparison-between-properties-and-indexers.md)  
  
- [Erişimci Erişilebilirliğini Kısıtlama](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Dizin](~/_csharplang/spec/classes.md#indexers) leyiciler'e bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](../classes-and-structs/properties.md)
