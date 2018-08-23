---
title: override (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: c0fdb777c4f5a64dbc92f6afe78cdb714585efe0
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753930"
---
# <a name="override-c-reference"></a>override (C# Başvurusu)
`override` Değiştiricisi, genişletme veya soyut ya da sanal uygulaması devralınan yöntemi, özelliği, dizin oluşturucusu veya olayı değiştirmek için gereklidir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `Square` sınıfı, geçersiz kılınan bir uygulamasını sağlaması gerektiği `Area` çünkü `Area` Özet devralınan `ShapesClass`:  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 Bir `override` yöntemi, bir temel sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar. Yöntemi tarafından geçersiz kılınan bir `override` bildirimi geçersiz kılınan taban yöntemi bilinir. Geçersiz kılınan taban yöntemi olarak aynı imzaya sahip olmalıdır `override` yöntemi. Devralma hakkında daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Sanal olmayan veya statik bir yöntemi geçersiz kılınamıyor. Geçersiz kılınan taban yöntemi olmalıdır `virtual`, `abstract`, veya `override`.  
  
 Bir `override` bildirimi erişilebilirliğini değiştiremez `virtual` yöntemi. Her iki `override` yöntemi ve `virtual` yöntemi aynı olmalıdır [erişim düzeyi değiştiricisi](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Kullanamazsınız `new`, `static`, veya `virtual` değiştirmek için değiştiriciler bir `override` yöntemi.  
  
 Devralınan özellik olarak geçersiz kılan bir özellik bildirimi tam olarak aynı erişim değiştiricisi, türü ve adı belirtmeniz gerekir ve geçersiz kılınan özelliğin olmalıdır `virtual`, `abstract`, veya `override`.  
  
 Nasıl kullanılacağı hakkında daha fazla bilgi için `override` anahtar sözcüğü, bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="example"></a>Örnek  
 Bu örnek adlı bir temel sınıf tanımlar `Employee`ve adlı bir türetilmiş sınıf `SalesEmployee`. `SalesEmployee` Sınıfı içeren ek bir alan `salesbonus`ve metot geçersiz kılmaları `CalculatePay` hesaba katması için.  
  
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
