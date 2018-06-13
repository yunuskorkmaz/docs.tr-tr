---
title: Özellikler (C# Programlama Kılavuzu)
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 47f8e978d81b4aec94482f0a295691b830c3698c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325168"
---
# <a name="properties-c-programming-guide"></a>Özellikler (C# Programlama Kılavuzu)

Bir özelliği okuma, yazma ya da bir özel alanın değerini hesaplamak için esnek bir mekanizma sağlayan bir üyesidir. Özellikler, ortak veri üyeleri olan, ancak bunlar adlı gerçekten özel yöntemler gibi kullanılabilir *erişimciler*. Bu verileri kolayca erişilmesini sağlar ve hala güvenlik ve esneklik yöntemlerin Yükselt yardımcı olur.  

## <a name="properties-overview"></a>Özelliklere genel bakış  
  
- Değerleri, uygulama veya doğrulama kodu gizleme sırasında ayarlama ve alma, ortak bir şekilde kullanıma sunmak için bir sınıf özelliklerini etkinleştirin.  
  
- A [almak](../../../csharp/language-reference/keywords/get.md) özelliği erişimcisi özellik değeri döndürmek için kullanılır ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) özelliği erişimcisi yeni bir değer atamak için kullanılır. Bu erişimciler farklı erişim düzeyleri olabilir. Daha fazla bilgi için bkz: [erişimci erişilebilirliğini kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
- [Değeri](../../../csharp/language-reference/keywords/value.md) tarafından atanan değer tanımlamak için kullanılan anahtar sözcüğü `set` erişimcisi.  
- Özellikler olabilir *okuma-yazma* (her ikisi de sahip oldukları bir `get` ve `set` erişimci), *salt okunur* (sahip oldukları bir `get` erişimci ancak hiçbir `set` erişimci), ya da *salt yazılır* (sahip oldukları bir `set` erişimci ancak hiçbir `get` erişimcisi). Salt yazılır özellikler nadir ve hassas verilere erişimi kısıtlamak için en yaygın olarak kullanılır.

- Hiçbir özel erişimci kodu gerektiren basit özellikler ifade gövdesi tanımları veya olarak uygulanabilir [otomatik uygulanan Özellikler](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).
 
## <a name="properties-with-backing-fields"></a>Alanları yedekleme ile özellikleri

Ayarlama ve özellik değerini almak için bir özel yedekleme alanını kullanarak bir özelliği uygulamak için bir temel düzeni içerir. `get` Erişimci özel alanın değerini döndürür ve `set` erişimci özel alan bir değer atamadan önce bazı veri doğrulaması gerçekleştirebilir. Döndürülen depolanan veya yüklenmeden önce her iki erişimciler Ayrıca verileri bazı dönüştürme ya da hesaplama gerçekleştirebilir.

Aşağıdaki örnekte bu deseni gösterilmektedir. Bu örnekte, `TimePeriod` sınıfı, bir zaman aralığı temsil eder. Sınıfı zaman aralığını saniye cinsinden adlı özel bir alanda dahili olarak depolar `seconds`. Adlı bir okuma-yazma özelliği `Hours` saat cinsinden zaman aralığı belirtmek müşteri sağlar. Hem `get` ve `set` erişimciler saatleri ve saniye arasında gerekli dönüştürme gerçekleştirin. Ayrıca, `set` erişimci verileri doğrular ve oluşturur bir <xref:System.ArgumentOutOfRangeException> saat sayısını geçersizse. 
   
 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  

 Özellik erişimcisi genellikle yalnızca atamak veya bir ifade sonuç döndüren tek satırlı bilgilerinin oluşur. Bu özellikleri ifade bodied üye olarak uygulayabilirsiniz. İfade gövdesi tanımları oluşur `=>` atayın veya özelliğinden almak için ifade arkasından simgesi.

 C# 6 ile başlayarak, salt okunur özellikler uygulayabilirsiniz `get` bir ifade bodied üye olarak erişimcisi. Bu durumda, hiçbiri `get` erişimci anahtar sözcüğü veya `return` anahtar sözcüğü kullanılır. Aşağıdaki örnek salt okunur uygulayan `Name` özelliği bir ifade bodied üye olarak.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 C# 7.0 ile başlayan hem `get` ve `set` erişimci ifade bodied üye olarak uygulanabilir. Bu durumda, `get` ve `set` anahtar sözcükleri bulunmalıdır. Aşağıdaki örnekte iki erişimciler ifade gövdesi tanımlarını kullanımını göstermektedir. Unutmayın `return` anahtar sözcüğü ile kullanılmaz `get` erişimcisi.
 
  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Otomatik uygulanan özellikler

Bazı durumlarda, özellik `get` ve `set` erişimciler yalnızca bir değer atadığınız değeri veya yedekleme alandan herhangi bir ek mantık eklemeden. Otomatik uygulanan özellikler kullanarak C# Derleyici şeffaf bir şekilde yedekleme alanını için sağladığınız yaparken kodunuzu basitleştirebilirsiniz. 

Bir özelliği hem de varsa, bir `get` ve `set` erişimci gerekir hem de otomatik uygulanan. Otomatik uygulanan bir özellik kullanarak tanımladığınız `get` ve `set` herhangi bir uygulaması sağlamadan anahtar sözcükler. Aşağıdaki örnek, dışında öncekinin yineler `Name` ve `Price` otomatik uygulanan özellikler. Bu örnek ayrıca parametreli Oluşturucusu kaldırır Not böylece `SaleItem` nesneleri varsayılan oluşturucu çağrısıyla şimdi başlatılır ve bir [Başlatıcı nesne](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>İlgili bölümler  
  
-   [Özellikleri Kullanma](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Arabirim Özellikleri](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Erişimci Erişilebilirliğini Kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [Otomatik Uygulanan Özellikler](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özellikleri Kullanma](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
 [get anahtar sözcüğü](../../../csharp/language-reference/keywords/get.md)    
 [Set anahtar sözcüğü](../../../csharp/language-reference/keywords/set.md)    
