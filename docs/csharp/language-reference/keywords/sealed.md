---
title: "sealed (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords: sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8248b451f0431286fdaba3583fc2031eb6cdbcd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sealed-c-reference"></a>sealed (C# Başvurusu)
Bir sınıfa uygulandığında `sealed` değiştiricisi ondan devralan diğer sınıflara engeller. Aşağıdaki örnekte, sınıf `B` sınıfından devralan `A`, ancak hiçbir sınıf sınıfı devralabilirsiniz `B`.  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 Aynı zamanda `sealed` değiştirici yöntem ya da sanal bir yöntem geçersiz kılan özellik ya da bir taban sınıf özelliği. Bu, sınıfından türetilen ve belirli sanal yöntemler veya özellikleri geçersiz kılmasını önlemek sınıflar izin vermenizi sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Z` devraldığı `Y` ancak `Z` sanal işlevi geçersiz kılınamaz `F` içinde bildirilen `X` ve içinde korumalı `Y`.  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 Yeni yöntemleri veya özellikleri bir sınıf tanımladığınızda, bunları olarak bildirerek değil önlemiş türetilen sınıflar engelleyebilirsiniz [sanal](../../../csharp/language-reference/keywords/virtual.md).  
  
 Kullanmak için bir hata olduğunu [soyut](../../../csharp/language-reference/keywords/abstract.md) değiştiricisi korumalı bir sınıf ile soyut bir sınıf soyut yöntemler veya özellikler uygulaması sağlayan bir sınıf tarafından devralınan gerekir çünkü.  
  
 Bir yöntemi veya özelliği, uygulandığında `sealed` değiştiricisi her zaman kullanılmalıdır [geçersiz kılma](../../../csharp/language-reference/keywords/override.md).  
  
 Yapılardan türetme çünkü bunlar devralınan olamaz.  
  
 Daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Daha fazla örnek için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 Önceki örnekte korumalı şu deyimi kullanarak sınıfından deneyebilecekleriniz:  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 Sonucu bir hata iletisi şudur:  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıfı, yöntemi veya özelliği korumaya verilmeyeceğini belirlemek için genellikle aşağıdaki iki noktaları dikkate alın:  
  
-   Olası faydaları sınıflardan türetme sınıfınız özelleştirme yeteneği elde.  
  
-   Sınıflardan türetme gibi sınıflar değiştirebileceği olası bir yol artık doğru şekilde çalıştıklarını veya olarak bekleniyordu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [Soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [geçersiz kılma](../../../csharp/language-reference/keywords/override.md)  
 [sanal](../../../csharp/language-reference/keywords/virtual.md)
