---
title: "Oluşturucular Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb9fcd1e4090da300de17c7fd808669ba51767c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-constructors-c-programming-guide"></a>Oluşturucular Kullanma (C# Programlama Kılavuzu)
Zaman bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md) olan oluşturulan kurucusu çağrılır. Oluşturucular sınıfta veya yapı aynı ada sahip ve bunlar genellikle yeni nesnenin veri üyeleri başlatma.  
  
 Aşağıdaki örnekte, adlı bir sınıf `Taxi` basit bir oluşturucu kullanılarak tanımlanır. Bu sınıf sonra ile örneği [yeni](../../../csharp/language-reference/keywords/new.md) işleci. `Taxi` Oluşturucusu tarafından çağrıldığında `new` işleci bellek hemen sonra yeni nesne için ayrılır.  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 Parametre almayan bir oluşturucu adlı bir *varsayılan oluşturucu*. Varsayılan Oluşturucu kullanarak bir nesne örneği olduğunda çağrılır `new` işleci ve bağımsız değişkenler için sağlanan `new`. Daha fazla bilgi için bkz: [örnek oluşturucuları](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Bir sınıf olmadığı sürece [statik](../../../csharp/language-reference/keywords/static.md), Oluşturucular, sınıf örneklemesi etkinleştirmek için C# Derleyici tarafından ortak varsayılan bir oluşturucu verilir olmadan sınıfları. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Bir sınıf oluşturucu özel, aşağıdaki gibi yaparak oluşturulmasını engelleyebilirsiniz:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 Daha fazla bilgi için bkz: [özel oluşturucular](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Oluşturucuları için [yapısı](../../../csharp/language-reference/keywords/struct.md) türleri sınıf Oluşturucular, benzer ancak `structs` bir derleyici tarafından otomatik olarak sağlandığından açık varsayılan bir oluşturucu içeremez. Bu oluşturucu, her bir alan başlatır `struct` varsayılan değerlere. Daha fazla bilgi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). Ancak, bu varsayılan kurucu yalnızca, çağrılan `struct` ile örneği `new`. Örneğin, bu kod için varsayılan oluşturucu kullanır <xref:System.Int32>, böylece tamsayı başlatıldığını garanti:  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Kullanmaz aşağıdaki kod, ancak bir derleyici hatasına neden olur `new`, ve başlatılmamış bir nesne kullanmayı dener:  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Alternatif olarak, nesneleri temel alarak `structs` (tüm yerleşik sayısal türler dahil) başlatıldı veya atanabilir ve aşağıdaki örnekte olduğu gibi kullanılır:  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Bu nedenle bir değer türü için varsayılan oluşturucu çağırma gerekli değildir.  
  
 Her iki sınıfları ve `structs` parametre almaz oluşturucular tanımlayabilirsiniz. Parametre almaz oluşturucular çağrılır, üzerinden bir `new` deyimi veya [temel](../../../csharp/language-reference/keywords/base.md) deyimi. Sınıfları ve `structs` hiçbiri varsayılan bir oluşturucu tanımlamak için gereklidir ve birden çok oluşturucular de tanımlayabilirsiniz. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 Bu sınıf, aşağıdaki deyimleri birini kullanarak oluşturulabilir:  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 Bir oluşturucu kullanın `base` bir temel sınıf aranacak anahtar. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 Blok Oluşturucu için yürütülmeden önce bu örnekte, temel sınıfın Oluşturucusu çağrılır. `base` Anahtar sözcüğü ile veya olmadan kullanılabilir. Oluşturucuya herhangi bir parametre için parametre olarak kullanılan `base`, veya bir ifadenin bir parçası olarak. Daha fazla bilgi için bkz: [temel](../../../csharp/language-reference/keywords/base.md).  
  
 Bir temel sınıf oluşturucu açıkça kullanarak çağrılmazsa türetilmiş bir sınıf içinde `base` anahtar sözcüğü, varsayılan oluşturucu varsa, adlandırılan örtük olarak. Bu aşağıdaki Oluşturucusu bildirimlerini etkili bir şekilde aynı anlamına gelir:  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 Bir temel sınıf varsayılan bir oluşturucu vermiyorsa türetilmiş sınıf temel oluşturucu için açık bir çağrı kullanılarak olmalısınız `base`.  
  
 Bir Oluşturucu kullanarak aynı nesnede başka bir oluşturucuyu çağırabileceği [bu](../../../csharp/language-reference/keywords/this.md) anahtar sözcüğü. Gibi `base`, `this` ile veya parametresiz kullanılabilir ve oluşturucuda herhangi bir parametre için parametre olarak kullanılabilir `this`, veya bir ifadenin bir parçası olarak. Örneğin, önceki örnekte ikinci oluşturucu kullanılarak yazılabilir `this`:  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 Kullanımını `this` anahtar sözcüğü önceki örnekte çağrılacak bu oluşturucuyu neden olur:  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 Oluşturucular işaretlenir olarak [ortak](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [içkorumalı](../../../csharp/language-reference/keywords/protected-internal.md)veya [korumalı özel](../../../csharp/language-reference/keywords/private-protected.md). Bu erişim değiştiricileri sınıfı kullanıcılarının sınıfı nasıl oluşturabileceğiniz tanımlayın. Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Bir Oluşturucu kullanarak statik bildirilebilir [statik](../../../csharp/language-reference/keywords/static.md) anahtar sözcüğü. Statik oluşturucular hemen statik alanları erişilen ve statik sınıf üyeleri başlatmak için genellikle kullanılan önce otomatik olarak adlandırılır. Daha fazla bilgi için bkz: [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
