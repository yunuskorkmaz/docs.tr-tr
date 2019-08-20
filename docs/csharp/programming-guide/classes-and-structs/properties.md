---
title: Özellikler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: dec4d4239fd1a953da6e64a1e1aff9593e2863e2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596146"
---
# <a name="properties-c-programming-guide"></a>Özellikler (C# Programlama Kılavuzu)

Bir özellik, özel bir alanın değerini okumak, yazmak veya hesaplamak için esnek bir mekanizma sağlayan bir üyesidir. Özellikler, ortak veri üyeleri gibi kullanılabilir, ancak aslında *erişimciler*olarak adlandırılan özel yöntemlerdir. Bu, verilere kolayca erişilmesine olanak sağlar ve yöntemlerin güvenliğini ve esnekliğini yükseltmeye devam eder.  

## <a name="properties-overview"></a>Özelliklere genel bakış  
  
- Özellikler, uygulama veya doğrulama kodunu gizlerken, değerleri almak ve ayarlamak için bir sınıfın ortak bir yöntemini kullanıma sunar.  
  
- [Get](../../language-reference/keywords/get.md) Property erişimcisi, özellik değerini döndürmek için kullanılır ve yeni bir değer atamak için bir [set](../../language-reference/keywords/set.md) özellik erişimcisi kullanılır. Bu erişimciler farklı erişim düzeylerine sahip olabilir. Daha fazla bilgi için bkz. [erişimci erişilebilirliğini kısıtlama](./restricting-accessor-accessibility.md).  
  
- [Value](../../language-reference/keywords/value.md) anahtar sözcüğü, `set` erişimci tarafından atanan değeri tanımlamak için kullanılır.  
- Özellikler *okuma-yazma* (hem a `get` hem `set` de erişimciye sahiptir), *salt okunurdur* (bir `get` erişimcisi vardır ancak `set` erişimci yoktur) ya da salt *yazılır* ( `set` erişimci, ancak erişimci `get` yok). Salt yazılır özellikler nadir ve hassas verilere erişimi kısıtlamak için en yaygın olarak kullanılır.

- Özel erişimci kodu gerektirmeyen basit özellikler, ifade gövde tanımları ya da [Otomatik uygulanan özellikler](./auto-implemented-properties.md)olarak uygulanabilir.
 
## <a name="properties-with-backing-fields"></a>Yedekleme alanları olan özellikler

Özelliği uygulamak için bir temel model, özellik değerini ayarlamak ve almak için özel bir yedekleme alanı kullanmayı içerir. Erişimci özel alanın değerini döndürür `set` ve özel alana bir değer atamadan önce erişimci bazı veri doğrulaması gerçekleştirebilir. `get` Her iki erişimci de verilerin depolanmadan veya döndürülmeden önce veri üzerinde bazı dönüştürme veya hesaplama işlemleri yapabilir.

Aşağıdaki örnekte bu desenler gösterilmektedir. Bu örnekte, `TimePeriod` sınıfı bir zaman aralığını temsil eder. Dahili olarak, sınıfı, zaman aralığını saniye cinsinden adlı `_seconds`özel bir alana depolar. Adlı `Hours` bir okuma-yazma özelliği, müşterinin saat cinsinden zaman aralığını belirtmesini sağlar. `get` Hem`set` hem de erişimcileri, saat ve saniyeler arasında gerekli dönüşümü gerçekleştirir. Ayrıca, `set` erişimci verileri doğrular ve saat sayısı geçersizse bir <xref:System.ArgumentOutOfRangeException> oluşturur. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  

 Özellik erişimcileri genellikle yalnızca bir ifadenin sonucunu atayan veya döndüren tek satırlık deyimlerden oluşur. Bu özellikleri ifade Bodied Üyeler olarak uygulayabilirsiniz. İfade gövdesi tanımları, `=>` sembolün önüne atanacak veya özelliğe alma ifadesi tarafından izlenen ifadeden oluşur.

 C# 6 ' dan itibaren, salt okuma özellikleri `get` erişimciyi ifade olarak uygulayabilir. Bu durumda, `get` erişimci anahtar kelimesi `return` ne de anahtar sözcük kullanılmaz. Aşağıdaki örnek, salt okunurdur `Name` özelliği bir ifade-Bodied üyesi olarak uygular.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 7,0 ile C# başlayarak, hem hem `get` de `set` erişimcisi ifade Bodied Üyeler olarak uygulanabilir. Bu durumda, `get` ve `set` anahtar sözcüklerin mevcut olması gerekir. Aşağıdaki örnek her iki erişimci için ifade gövde tanımlarının kullanımını gösterir. `return` Anahtar sözcüğünün`get` erişimciyle kullanılmadığını unutmayın.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Otomatik uygulanan özellikler

Bazı durumlarda, özellik `get` ve `set` erişimciler, ek bir mantık dahil etmeden bir destek alanından bir değer atar veya bir değer alır. Otomatik uygulanan özellikleri kullanarak, C# derleyicinin sizin için bir yedekleme alanı sunarak kodunuzu saydam bir şekilde sağlamasına gerek kalmadan kodunuzu basitleştirebilirsiniz. 

Bir özelliğin hem a `get` `set` hem de erişimcisi varsa, her ikisinin de otomatik olarak uygulanması gerekir. Herhangi bir uygulama sağlamadan `get` ve `set` anahtar sözcüklerini kullanarak otomatik uygulanan bir özellik tanımlarsınız. Aşağıdaki örnek, `Name` ve `Price` ' nin otomatik olarak uygulanan özellikler olması dışında, önceki birini yinelenir. Ayrıca, `SaleItem` nesnelerin parametresiz oluşturucuya ve bir [nesne başlatıcısına](object-and-collection-initializers.md)çağrısıyla başlatılmış olması için parametreli oluşturucuyu de kaldırdığına unutmayın.

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>İlgili bölümler  
  
- [Özellikleri Kullanma](./using-properties.md)  
  
- [Arabirim Özellikleri](./interface-properties.md)  
  
- [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Erişimci Erişilebilirliğini Kısıtlama](./restricting-accessor-accessibility.md)  
  
- [Otomatik Uygulanan Özellikler](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [Özellikler](~/_csharplang/spec/classes.md#properties) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikleri Kullanma](./using-properties.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [anahtar sözcüğü al](../../language-reference/keywords/get.md)
- [anahtar sözcük ayarla](../../language-reference/keywords/set.md)
