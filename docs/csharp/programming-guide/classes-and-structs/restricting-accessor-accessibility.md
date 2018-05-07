---
title: Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: bf9ead7934630d3974657107ca38e08bbd3bed85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)
[Almak](../../../csharp/language-reference/keywords/get.md) ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) bir özellik veya dizin bölümlerini çağrılır *erişimciler*. Varsayılan olarak bu erişimciler aynı görünürlüğe sahip veya erişim düzeyi:, ait oldukları özelliği ya da dizin oluşturucu. Daha fazla bilgi için bkz: [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md). Ancak, bazen bu erişimciler birine erişimi kısıtlamak yararlıdır. Genellikle, bu erişilebilirliğini kısıtlama içerir `set` tutma sırasında erişimcisi `get` erişimci genel olarak erişilebilir. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 Bu örnekte, bir özellik olarak adlandırılan `Name` tanımlayan bir `get` ve `set` erişimcisi. `get` Erişimci alır özelliğin kendisine erişilebilirlik düzeyi `public` bu durumda, while `set` erişimci açıkça kısıtlanmış uygulayarak [korumalı](../../../csharp/language-reference/keywords/protected.md) erişim değiştiricisi erişimci kendisi.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Erişim değiştiricileri kısıtlamalar  
 Özellikler ve dizin oluşturucular erişimci değiştiricilerini kullanarak bu koşullara tabi şöyledir:  
  
-   Bir arabirim veya açık bir erişimci değiştiricileri kullanamazsınız [arabirimi](../../../csharp/language-reference/keywords/interface.md) üye uygulama.  
  
-   Yalnızca özellik veya dizin oluşturucu her ikisi de varsa erişimcisi değiştiricileri kullanabilirsiniz `set` ve `get` erişimciler. Bu durumda, değiştiricisi birinde yalnızca iki erişimciler izin verilir.  
  
-   Özellik veya dizin oluşturucu varsa bir [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) değiştiricisi, erişimci değiştiricisi eşleşmelidir geçersiz kılınan erişimci erişimcisi varsa.  
  
-   Erişilebilirlik düzeyi erişimcisi üzerinde erişilebilirlik düzeyi özelliği veya dizin oluşturucu kendisini daha kısıtlayıcı olmalıdır.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Erişimciler geçersiz kılma üzerinde erişim değiştiricileri  
 Bir özellik veya dizin oluşturucu geçersiz kıldığınızda, geçersiz kılınan erişimciler geçersiz kılma koda erişilebilir olması gerekir. Ayrıca, hem özelliği/dizin oluşturucu erişilebilirlik düzeyi ve erişimciler, karşılık gelen geçersiz kılınan özelliği/dizin oluşturucu ve erişimciler aynı olmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a>Arabirimler uygulama  
 Bir arabirim için bir erişimci kullandığınızda, bir erişim değiştiricisi erişimcisi olmayabilir. Ancak, bir erişimci gibi kullanılarak arabirimini uygulayan varsa `get`, diğer erişimcisi aşağıdaki örnekteki gibi bir erişim değiştiricisi sahip olabilir:  
  
 [!code-csharp[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a>Erişimci erişilebilirlik etki alanı  
 Erişimci üzerinde bir erişim değiştiricisi kullanırsanız [erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md) erişimcisine bu değiştirici tarafından belirlenir.  
  
 Bir erişim değiştiricisi erişimcisine kullanmadıysanız erişimci erişilebilirlik etki alanı özelliği veya dizin oluşturucu erişilebilirlik düzeyi tarafından belirlenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç sınıfları içerir `BaseClass`, `DerivedClass`, ve `MainClass`. İki özellik vardır `BaseClass`, `Name` ve `Id` hem sınıfları. Örnek gösterir nasıl özelliği `Id` üzerinde `DerivedClass` özelliği tarafından gizli `Id` üzerinde `BaseClass` kullandığınızda kısıtlayıcı erişim değiştiricisi gibi [korumalı](../../../csharp/language-reference/keywords/protected.md) veya [ özel](../../../csharp/language-reference/keywords/private.md). Bu nedenle, atadığınızda bu özellik, özellik değerleri üzerinde `BaseClass` sınıfı yerine çağrılır. Tarafından erişim değiştiricisi değiştirme [ortak](../../../csharp/language-reference/keywords/public.md) özelliği erişilebilir hale getirir.  
  
 Bu örnek ayrıca gösteren bir kısıtlayıcı erişim değiştiricisi gibi `private` veya `protected`, `set` erişimcisine `Name` özelliğinde `DerivedClass` erişimci erişimi engeller ve atadığınızda, içerik için bir hata oluşturur .  
  
 [!code-csharp[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a>Açıklamalar  
 Bildirim değiştirirseniz dikkat `new private string Id` tarafından `new public string Id`, çıktı alın:  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
 [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
