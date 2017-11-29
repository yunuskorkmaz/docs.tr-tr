---
title: "Dizin Oluşturucular (C# Programlama Kılavuzu)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: db49a602b83940cab3f87dea17accb92a2be825d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="indexers-c-programming-guide"></a>Dizin Oluşturucular (C# Programlama Kılavuzu)

Dizin oluşturucular sınıfta veya yapı yalnızca diziler gibi dizine örneklerini izin verin. Dizinli değer ayarlayın veya açıkça türü veya örnek bir üye belirtilmeden alınamıyor. Dizin oluşturucular benzer [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md) kendi erişimciler parametre almaz ancak bu.  
 
 Aşağıdaki örnekte basit ile genel bir sınıf tanımlar [almak](../../../csharp/language-reference/keywords/get.md) ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) atamak ve değerleri almak için erişimci yöntemleri. `Program` Sınıfı, dizeleri depolamak için bu sınıfının bir örneğini oluşturur.  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  Daha fazla örnek için bkz: [ilgili bölümler](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları  
 
Bir oluşturucunun get veya set erişimcisi döndürür veya bir değer ayarlar tek bir deyimde oluşması için yaygın bir durumdur. İfade bodied üyeleri bu senaryoyu desteklemek için basitleştirilmiş bir sözdizimi sağlar. C# 6 ile başlayarak, bir salt okunur dizin oluşturucu aşağıdaki örnekte gösterildiği gibi bir ifade bodied üye olarak uygulanabilir.

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

Unutmayın `=>` ifade gövde ve tanıtır `get` anahtar sözcüğü kullanılmaz. 

C# 7, hem get'ile başlayan ve set erişimcisi uygulanan bir ifade bodied üyesi olabilir. Bu durumda, her ikisi de `get` ve `set` anahtar sözcükleri kullanılmalıdır. Örneğin:

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a>Dizin Oluşturuculara Genel Bakış  
  
-   Dizin oluşturucular dizilerine benzer bir şekilde dizine nesneleri sağlar.  
  
-   A `get` erişimci değeri döndürür. A `set` erişimci değeri atar.  
  
-   [Bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğü dizin oluşturucu tanımlamak için kullanılır.  
  
-   [Değeri](../../../csharp/language-reference/keywords/value.md) tarafından atanan değer tanımlamak için kullanılan anahtar sözcüğü `set` dizin oluşturucu.  
  
-   Dizin oluşturucular tarafından bir tamsayı değeri sıralanması gerekmez; Bu size, belirli arama mekanizması tanımlamak nasıl bağlıdır.  
  
-   Dizin oluşturucular aşırı yüklenmiş.  
  
-   Dizin oluşturucular birden fazla biçimsel parametresi, örneğin, iki boyutlu bir dizi erişirken olabilir.  
  
##  <a name="BKMK_RelatedSections"></a>İlgili bölümler  
  
-   [Dizin oluşturucular kullanma](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Arabirimlerdeki dizin oluşturucular](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Özellikler ve dizin oluşturucular arasında karşılaştırma](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Erişimci erişilebilirliğini kısıtlama](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)
