---
title: Özellikler - C# Programlama Kılavuzu
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: ee530e981e0c85302b2b11cc739d6c51d6650ddd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170110"
---
# <a name="properties-c-programming-guide"></a>Özellikler (C# Programlama Kılavuzu)

Özellik, özel bir alanın değerini okumak, yazmak veya hesaplamak için esnek bir mekanizma sağlayan bir üyedir. Özellikler, genel veri üyeleri gibi kullanılabilir, ancak aslında *erişimci*olarak adlandırılan özel yöntemlerdir. Bu, verilere kolayca erişilmesini sağlar ve yöntemlerin güvenliğini ve esnekliğini desteklemeye yardımcı olur.  

## <a name="properties-overview"></a>Özelliklere genel bakış  
  
- Özellikler, uygulama veya doğrulama kodunu gizlerken sınıfın değerleri alma ve ayarlama nın genel bir yolunu ortaya çıkarmasını sağlar.  
  
- Özellik değerini döndürmek için bir [özellik](../../language-reference/keywords/get.md) erişime erişime erişim, yeni bir değer atamak için [ayarlanmış](../../language-reference/keywords/set.md) bir özellik erişimcisi kullanılır. Bu erişime erişim düzeyleri farklı olabilir. Daha fazla bilgi için [bkz.](./restricting-accessor-accessibility.md)  
  
- [Değer](../../language-reference/keywords/value.md) anahtar `set` kelimesi, erişimci tarafından atanan değeri tanımlamak için kullanılır.  
- Özellikler *okuma-yazma* (hem bir `get` hem `set` de bir erişimciye sahiptir), *salt okunur* `get` (erişime erişime sahiptirler ancak `set` erişime `get` erişimyoktur) veya yalnızca *yazma* `set` (bir erişime erişime sahiptirler, ancak erişime erişime erişimyoktur). Yalnızca yazma özellikleri nadirdir ve en yaygın olarak hassas verilere erişimi kısıtlamak için kullanılır.

- Özel erişim kodu gerektirmeyen basit özellikler, ifade gövdesi tanımları veya [otomatik olarak uygulanan özellikler](./auto-implemented-properties.md)olarak uygulanabilir.

## <a name="properties-with-backing-fields"></a>Destek alanlarına sahip özellikler

Bir özelliği uygulamak için temel bir desen, özellik değerini ayarlamak ve almak için özel bir destek alanı kullanmayı içerir. Erişimci `get` özel alanın değerini döndürür `set` ve erişimci özel alana bir değer atamadan önce bazı veri doğrulama gerçekleştirebilir. Her iki erişimci de depolanmadan veya döndürülmeden önce veriler üzerinde bazı dönüşüm veya hesaplama gerçekleştirebilir.

Aşağıdaki örnekte bu desen gösteriş göstermektedir. Bu örnekte, `TimePeriod` sınıf bir zaman aralığını temsil eder. Dahili olarak, sınıf zaman aralığını saniyeler `_seconds`içinde özel bir alanda depolar. Adlandırılmış `Hours` bir okuma-yazma özelliği, müşterinin saat aralığını belirtmesine olanak tanır. Hem `get` `set` erişimedenler hem de erişimedenler, saat ve saniye ler arasında gerekli dönüşümü gerçekleştirirler. Buna ek `set` olarak, erişimci verileri doğrular <xref:System.ArgumentOutOfRangeException> ve saat sayısı geçersizse bir atar.

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  

 Özellik erişime girenler genellikle bir ifadenin sonucunu atayana veya döndüren tek satırlı ifadelerden oluşur. Bu özellikleri ifade gövdeli üyeler olarak uygulayabilirsiniz. İfade gövdesi tanımları, `=>` özellik için atama veya almak için ifade takip sembolü oluşur.

 C# 6 ile başlayarak, salt `get` okunur özellikler, erişime gireni ifade gövdeli bir üye olarak uygulayabilir. Bu durumda, ne `get` erişimci anahtar `return` kelime ne de anahtar kelime kullanılır. Aşağıdaki örnek, ifade gövdeli `Name` bir üye olarak salt okunur özelliğini uygular.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 C# 7.0 ile başlayarak, `set` hem erişimci `get` hem de ifade gövdeli üye olarak uygulanabilir. Bu durumda, `get` anahtar `set` kelimeler ve anahtar kelimeler mevcut olmalıdır. Aşağıdaki örnekte, her iki aksesuar için ifade gövdesi tanımlarının kullanımı gösterilmektedir. Anahtar kelimenin `return` `get` erişimciyle birlikte kullanılmadığını unutmayın.

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Otomatik uygulanan özellikler

Bazı durumlarda, `get` özellik `set` ve erişimedenler herhangi bir ek mantık dahil olmadan bir destek alanına bir değer atamak veya almak. Otomatik olarak uygulanan özellikleri kullanarak, C# derleyicisinin sizin için destek alanını saydam olarak sağlamasına sahip olurken kodunuzu basitleştirebilirsiniz.

Bir özellikhem bir `get` hem `set` de bir erişimci varsa, her ikisi de otomatik olarak uygulanmalıdır. Herhangi bir uygulama sağlamadan `get` anahtar kelimeleri `set` ve anahtar kelimeleri kullanarak otomatik olarak uygulanan bir özelliği tanımlarsınız. Aşağıdaki örnek, bunun `Name` dışında bir öncekini yineler ve `Price` otomatik olarak uygulanan özelliklerdir. Örneğin parametreli oluşturucuyu da kaldırdığını, `SaleItem` böylece nesnelerin parametresiz oluşturucuya ve nesne baş [harflerine](object-and-collection-initializers.md)bir çağrı yla baş harflere başlatIflaştırıladığını unutmayın.

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>İlgili bölümler  
  
- [Özellikleri Kullanma](./using-properties.md)  
  
- [Arayüz Özellikleri](./interface-properties.md)  
  
- [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Erişimci Erişilebilirliğini Kısıtlama](./restricting-accessor-accessibility.md)  
  
- [Otomatik Uygulanan Özellikler](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Özellikler'e](~/_csharplang/spec/classes.md#properties) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikleri Kullanma](./using-properties.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [anahtar kelime alma](../../language-reference/keywords/get.md)
- [anahtar kelime yi ayarlama](../../language-reference/keywords/set.md)
