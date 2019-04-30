---
title: Özellikler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 260c9e362281ba7996dc834ab47d7beb2755b636
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703497"
---
# <a name="properties-c-programming-guide"></a>Özellikler (C# Programlama Kılavuzu)

Bir özelliği okuma, yazma veya özel bir alanın değerini hesaplamak için esnek bir mekanizma sağlayan bir üyesidir. Bunlar genel veri üyeleri, ancak bunlar gerçekten özel yöntemler olarak adlandırılan yokmuş gibi özellikleri kullanılabilir *erişimcileri*. Bu, verileri kolayca erişilmesini sağlar ve yine de güvenlik ve esneklik yöntemlerin yardımcı olur.  

## <a name="properties-overview"></a>Özelliklere genel bakış  
  
- Özellikleri alma ve uygulama ya da doğrulama kodu gizleyerek değerleri ayarlama, genel bir şekilde kullanıma sunmak bir sınıf sağlar.  
  
- A [alma](../../../csharp/language-reference/keywords/get.md) özellik erişimcisi özellik değeri döndürmek için kullanılır ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) özellik erişimcisi yeni bir değer atamak için kullanılır. Bunlar farklı erişim düzeylerine sahip olabilir. Daha fazla bilgi için [erişimci erişilebilirliğini kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
- [Değer](../../../csharp/language-reference/keywords/value.md) tarafından atanan değerin tanımlamak için kullanılan anahtar sözcüğü `set` erişimcisi.  
- Özellikleri olabilir *okuma-yazma* (her ikisi de sahip bir `get` ve `set` erişimci), *salt okunur* (sahip oldukları bir `get` erişimci ancak Hayır `set` erişimci), veya *salt yazılır* (sahip oldukları bir `set` erişimci, ancak Hayır `get` erişimci). Salt yazılır özellikler nadirdir ve hassas verilere erişimi kısıtlamak için en yaygın olarak kullanılır.

- İfade gövdesi tanımları veya olarak özel erişimci kod gerektiren basit özellikleri uygulanabilir [otomatik uygulanan Özellikler](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).
 
## <a name="properties-with-backing-fields"></a>Destek alanları ile özellikleri

Uygulayan bir özellik için bir temel düzeni, özel destek alanı ayarlama ve özellik değerini almak için kullanmayı içerir. `get` Erişimcisi özel alanın değerini döndürür ve `set` erişimcisi özel alanın bir değer atamadan önce birkaç veri doğrulaması gerçekleştirebilir. Döndürülen depolanmış veya yüklenmeden önce her iki erişimcisi ayrıca veriler üzerinde bazı dönüştürme veya hesaplama gerçekleştirebilir.

Aşağıdaki örnek, bu düzen gösterilmiştir. Bu örnekte, `TimePeriod` sınıfı, bir zaman aralığını temsil eder. Sınıfı zaman aralığını saniye cinsinden adlı özel bir alanda dahili olarak depolayan `_seconds`. Adlı bir okuma-yazma özelliği `Hours` saat cinsinden zaman aralığı belirtmesine olanak tanır. Hem `get` ve `set` erişimcileri saat ve saniye arasında gerekli dönüşüm gerçekleştirin. Ayrıca, `set` erişimci verileri doğrular ve oluşturur bir <xref:System.ArgumentOutOfRangeException> varsa saat sayısı geçersiz. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  

 Özellik erişimcileri, genellikle yalnızca atamak veya bir ifadenin sonucu tek satır bilgilerinin oluşur. İfade gövdeli üyeler bu özellikleri uygulayabilir. İfade gövdesi tanımları oluşur `=>` simgesiyle atayın veya özelliğin almak için ifadeye göre.

 C# 6 ile başlayarak, salt okunur özellikler uygulayabilirsiniz `get` bir ifade gövdeli üyesi erişimcisi. Bu durumda, hiçbiri `get` erişimci anahtar sözcüğü ya da `return` anahtar sözcüğü kullanılır. Aşağıdaki örnek salt okunur uygulayan `Name` özelliği bir ifade gövdeli üyesi olarak.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 C# 7.0 ile başlayarak hem `get` ve `set` erişimci ifade gövdeli üyeler uygulanabilir. Bu durumda, `get` ve `set` anahtar sözcükleri mevcut olmalıdır. Aşağıdaki örnek, her iki erişimcisi için ifade gövdesi tanımları kullanımını gösterir. Unutmayın `return` anahtar sözcüğü ile kullanılmaz `get` erişimcisi.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Otomatik uygulanan özellikler

Bazı durumlarda, özellik `get` ve `set` erişimciler yalnızca bir değer atayın veya ilave bir mantık dahil olmak üzere yedekleme alanından bir değer almak. Otomatik uygulanan özellikler kullanarak, yedekleme alanını şeffaf bir şekilde sağlar C# derleyicisini yaparken kodunuzu basitleştirebilirsiniz. 

Bir özellik hem de varsa bir `get` ve `set` erişimci gerekir hem de otomatik olarak uygulanan. Otomatik uygulanan bir özellik kullanarak tanımladığınız `get` ve `set` herhangi bir uygulama sağlamadan anahtar sözcükleri. Aşağıdaki örnek dışında Öncekine yineler `Name` ve `Price` otomatik uygulanan özellikler. Bu örnek ayrıca parametreli bir kurucu kaldırır Not böylece `SaleItem` nesneleri parametresiz bir oluşturucu çağrısı ile artık başlatılır ve bir [nesne Başlatıcı](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>İlgili bölümler  
  
- [Özellikleri Kullanma](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
- [Arabirim Özellikleri](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
- [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
- [Erişimci Erişilebilirliğini Kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
- [Otomatik Uygulanan Özellikler](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [özellikleri](~/_csharplang/spec/classes.md#properties) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Özellikleri Kullanma](../../../csharp/programming-guide/classes-and-structs/using-properties.md)
- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)
- [get anahtar sözcüğü](../../../csharp/language-reference/keywords/get.md)
- [Set anahtar sözcüğü](../../../csharp/language-reference/keywords/set.md)
