---
title: -Erişimci erişilebilirliğini kısıtlama C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: c15b4939306b79f843b22dc808d88bf3d20ed555
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703419"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)
[Alma](../../../csharp/language-reference/keywords/get.md) ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) bölümlerini özelliğin veya dizin oluşturucu çağrılır *erişimcileri*. Varsayılan olarak, özellik veya dizin oluşturucu ait oldukları aynı görünürlük veya erişim düzeyini bu erişimcilerine sahip. Daha fazla bilgi için [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md). Ancak, bazen bu erişimcileri birine erişimi kısıtlamak yararlıdır. Genellikle, bu erişilebilirliğini kısıtlama içerir `set` tutma sırasında erişimci `get` erişimci genel olarak erişilebilir. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 Bu örnekte, bir özelliğin çağırılır `Name` tanımlayan bir `get` ve `set` erişimcisi. `get` Erişimci özelliğin kendisine erişilebilirlik düzeyi alır `public` bu durumda, while `set` erişimci açıkça kısıtlanan uygulayarak [korumalı](../../../csharp/language-reference/keywords/protected.md) erişim değiştiricisi erişimci kendisi.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Erişim değiştiricileri kısıtlamaları  
 Erişimci değiştiriciler özellikleri veya dizin oluşturucuları kullanarak bu koşullara tabi olan:  
  
- Bir arabirim veya açık bir erişimci değiştiriciler kullanamazsınız [arabirimi](../../../csharp/language-reference/keywords/interface.md) üye uygulaması.  
  
- Erişimci değiştiricileri yalnızca özellik veya dizin oluşturucusu hem de varsa kullanabilirsiniz `set` ve `get` erişimcileri. Bu durumda, değiştirici, yalnızca iki erişimci her biri izin verilir.  
  
- Özellik veya dizin oluşturucusu varsa bir [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) değiştiricisi, erişimci değiştiricisi eşleşmelidir geçersiz kılınan erişimcisinin erişimcisi varsa.  
  
- Erişimci erişilebilirliği düzeyde erişilebilirlik düzeyi özelliği veya dizin oluşturucu kendisini daha kısıtlayıcı olmalıdır.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Erişimciler geçersiz kılma üzerinde erişim değiştiricileri  
 Bir özellik veya dizin oluşturucu geçersiz kıldığınızda, geçersiz kılınan erişimcileri geçersiz kılma koda erişilebilir olması gerekir. Ayrıca, hem özellik/dizin oluşturucu ve onun erişimcilerinin erişilebilirliği, karşılık gelen geçersiz kılınan özelliğin/dizin oluşturucu ve onun erişimcilerinin eşleşmesi gerekir. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a>Arabirimleri uygulama  
 Bir arabirim uygulamak için bir erişimci kullandığınızda, bir erişim değiştiricisidir erişimci olmayabilir. Ancak, bir erişimci gibi kullanarak arabirim uygular, `get`, aşağıdaki örnekte olduğu gibi bir erişim değiştiricisidir diğer erişimcisi olabilir:  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a>Erişimcisinin erişilebilirlik etki alanı  
 Erişimci üzerinde bir erişim değiştiricisidir kullanırsanız [erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md) erişimcisine bu değiştirici tarafından belirlenir.  
  
 Bir erişim değiştiricisidir erişimcisine kullanmadıysanız erişimcisinin erişilebilirlik etki alanı özellik veya dizin oluşturucu erişilebilirlik düzeyi tarafından belirlenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç sınıfları içerir. `BaseClass`, `DerivedClass`, ve `MainClass`. İki özelliği vardır `BaseClass`, `Name` ve `Id` hem sınıfları. Örnek gösterir nasıl özelliği `Id` üzerinde `DerivedClass` özelliğiyle gizlenebilir `Id` üzerinde `BaseClass` kullandığınızda bir kısıtlayıcı erişim değiştiricisi gibi [korumalı](../../../csharp/language-reference/keywords/protected.md) veya [ özel](../../../csharp/language-reference/keywords/private.md). Bu nedenle, atadığınızda bu özellik, özellik değerleri üzerinde `BaseClass` sınıfı yerine çağrılır. Erişim değiştiricisi ile değiştirerek [genel](../../../csharp/language-reference/keywords/public.md) özelliği erişilebilir hale getirir.  
  
 Bu örnek ayrıca gösteren bir kısıtlayıcı erişim değiştiricisi gibi `private` veya `protected`, `set` erişimcisine `Name` özelliğinde `DerivedClass` erişimciye erişimi engeller ve atadığınız bir hata oluşturur .  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a>Açıklamalar  
 Bildirimi değiştirirseniz dikkat `new private string Id` tarafından `new public string Id`, çıkış alırsınız:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)
- [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
