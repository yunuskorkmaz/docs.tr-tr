---
title: override (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 8f692dfdf8bd34ddb62623d86ec3dadd2b8dead3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="override-c-reference"></a>override (C# Başvurusu)
`override` Genişletmek veya bir devralınan yöntemi, özelliği, dizin oluşturucu veya olay soyut veya sanal uyarlamasını değiştirmek için değiştiricisi gereklidir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `Square` sınıfı geçersiz kılınan uygulaması sağlamalıdır `Area` çünkü `Area` Özet devralınan `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 Bir `override` yöntemi bir taban sınıftan devralınan bir üyenin yeni bir uygulama sağlar. Tarafından geçersiz kılınır yöntemi bir `override` bildirimi geçersiz kılınan temel yöntemi olarak bilinir. Geçersiz kılınan temel yöntemi olarak aynı imzaya sahip olmalıdır `override` yöntemi. Devralma hakkında daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Sanal olmayan veya statik yöntemi geçersiz kılamaz. Geçersiz kılınan temel yöntemi olmalıdır `virtual`, `abstract`, veya `override`.  
  
 Bir `override` bildirimi erişilebilirliğini değiştiremiyor `virtual` yöntemi. Her iki `override` yöntemi ve `virtual` yöntemi aynı olması gerekir [erişim düzeyi değiştiricisi](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Kullanamazsınız `new`, `static`, veya `virtual` değiştirmek için değiştiricileri bir `override` yöntemi.  
  
 Bir geçersiz kılma özellik bildirimi tam olarak aynı erişim değiştiricisi, türü ve adı devralınan özelliği olarak belirtmeniz gerekir ve geçersiz kılınan özelliği olmalıdır `virtual`, `abstract`, veya `override`.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `override` anahtar sözcüğü, bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir temel sınıf tanımlar `Employee`ve adlı türetilmiş bir sınıf `SalesEmployee`. `SalesEmployee` Sınıfı içeren bir ek özellik `salesbonus`ve yöntemini geçersiz kılar `CalculatePay` dikkate almanız için.  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
