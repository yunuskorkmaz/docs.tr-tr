---
title: 'Dizin oluşturucular - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
  - cs.indexers
helpviewer_keywords:
  - 'indexers [C#]'
  - 'C# language, indexers'
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
---
# <a name="indexers-c-programming-guide"></a>Dizin Oluşturucular (C# Programlama Kılavuzu)

Dizin oluşturucular bir sınıf veya yapı dizileri gibi yeni dizine örneklerini sağlar. Dizinli değerin ayarlanması veya açıkça bir tür veya örnek üye belirtilmeden alınır. Dizin oluşturucular benzer [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md) dışında kendi erişimcileri parametre alır.  
 
 Aşağıdaki örnek, basit ile genel bir sınıf tanımlar [alma](../../../csharp/language-reference/keywords/get.md) ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) atamak ve değerleri almak için erişimci metotlarını. `Program` Sınıfı, dizeleri depolamak için bu sınıfın bir örneğini oluşturur.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  Daha fazla örnek için bkz. [ilgili bölümler](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  
 
Bir oluşturucunun get veya set erişimcisi döndürür veya bir değer ayarlar tek bir deyimde oluşmalıdır için yaygın bir durumdur. İfade gövdeli üyeler bu senaryoyu desteklemek için basitleştirilmiş bir sözdizimi sağlar. C# 6 ile başlayarak, aşağıdaki örnekte gösterildiği gibi bir ifade gövdeli üyesi olarak bir salt okunur dizin oluşturucu uygulanabilir.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Unutmayın `=>` ifade gövdesi ve `get` anahtar sözcüğü kullanılmaz. 

C# 7.0, hem get ile başlayan ve set erişimcisi olabilir uygulanan bir ifade gövdeli üyeler. Bu durumda, her ikisi de `get` ve `set` anahtar sözcükleri kullanılmalıdır. Örneğin:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Dizin Oluşturuculara Genel Bakış  
  
-   Dizin oluşturucular nesneleri dizilere benzer şekilde dizinlenmesini sağlar.  
  
-   A `get` erişimcisinin bir değer döndürür. A `set` erişimcisinin bir değer atar.  
  
-   [Bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğü, dizin oluşturucuyu tanımlamak için kullanılır.  
  
-   [Değer](../../../csharp/language-reference/keywords/value.md) tarafından atanan değerin tanımlamak için kullanılan anahtar sözcüğü `set` dizin oluşturucu.  
  
-   Dizin oluşturucular bir tamsayı değeri tarafından dizine gerekmez; size özel arama mekanizması tanımlama bağlıdır.  
  
-   Dizin oluşturucular aşırı yüklenebilir.  
  
-   Dizin oluşturucular birden fazla biçimsel parametre, örneğin, iki boyutlu bir dizi erişirken olabilir.  
  
## <a name="BKMK_RelatedSections"></a> İlgili bölümler  
  
-   [Dizin Oluşturucular Kullanma](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Arabirimlerdeki Dizin Oluşturucular](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Erişimci Erişilebilirliğini Kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [dizin oluşturucular](~/_csharplang/spec/classes.md#indexers) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)
