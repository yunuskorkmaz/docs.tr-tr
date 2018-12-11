---
title: Örnek oluşturucuları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 5cc7c06a763c4b274b154afc581e495a7e2aa09b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241661"
---
# <a name="instance-constructors-c-programming-guide"></a>Örnek Oluşturucuları (C# Programlama Kılavuzu)
Örnek oluşturucuları oluşturup kullandığınızda tüm örnek üye değişkenlerini başlatmak için kullanılan [yeni](../../../csharp/language-reference/keywords/new.md) ifade bir nesne oluşturmak için bir [sınıfı](../../../csharp/language-reference/keywords/class.md). Başlatmak için bir [statik](../../../csharp/language-reference/keywords/static.md) sınıf veya bir statik olmayan sınıf içinde statik değişkenler bir statik Oluşturucu tanımlamanız gerekir. Daha fazla bilgi için [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 Aşağıdaki örnek, bir örnek oluşturucusunda gösterir:  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Anlaşılsın diye, bu sınıf, ortak alanları içerir. Bir programda herhangi bir yerde herhangi bir yöntemi Kısıtlanmamış ve doğrulanmamış bir nesnenin iç çalışmalarına değineceğiz erişimi verdiğinden, ortak alanları kullanımını önerilen bir programlama uygulama değil. Veri üyeleri, genellikle özel olmalıdır ve yalnızca sınıfı yöntemleri ve özellikleri erişilmelidir.  
  
 Bir nesne dayalı olduğunda, bu örneği Oluşturucu çağrılır `CoOrds` sınıf oluşturulur. Hiçbir bağımsız değişkeni alır, bu bir adlı gibi bir oluşturucu bir *varsayılan oluşturucu*. Ancak, genellikle ek oluşturucular sağlamak için yararlı olur. Örneğin, bir oluşturucuya ekleyebiliriz `CoOrds` veri üyeleri için başlangıç değerlerini belirtmek sağlıyor sınıfı:  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Böylece `CoOrd` varsayılan veya özel ilk değerleri ile oluşturulan nesnelere şöyle:  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Bir sınıf bir oluşturucu yoksa, bir varsayılan oluşturucu otomatik olarak oluşturulur ve varsayılan değerler nesne alanları başlatmak için kullanılır. Örneğin, bir [int](../../../csharp/language-reference/keywords/int.md) 0 olarak başlatılır. Varsayılan değerleri hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). Bu nedenle, çünkü `CoOrds` sınıf varsayılan oluşturucusuna tüm veri üyeleri sıfırdan başlatır, sınıf şeklini değiştirmeden tamamen kaldırılabilir. Birden çok oluşturucuları kullanarak tam bir örnek daha sonra bu konudaki örnek 1'de sağlanan ve otomatik olarak oluşturulan bir oluşturucu örneği örnek 2'de sağlanır.  
  
 Örnek oluşturucuları, temel sınıfların örnek oluşturucuları çağırmak için de kullanılabilir. Sınıf oluşturucu başlatıcı aracılığıyla temel sınıfın Oluşturucusu gibi çağırabilirsiniz:  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 Bu örnekte, `Circle` sınıfı tarafından sağlanan oluşturucusu için RADIUS ve yüksekliğini temsil eden değerleri geçirir `Shape` içinden `Circle` türetilir. Kullanarak bir tam örnek `Shape` ve `Circle` bu konudaki örnek 3 olarak görünür.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnek, iki sınıf oluşturucuları, bir bağımsız değişkenler olmadan ve iki bağımsız değişkeni ile tek bir sınıfı gösterir.  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Örnek 2  
 Bu örnekte, sınıf `Person` durumda bir varsayılan oluşturucu otomatik olarak sağlanır ve alanları varsayılan değerlerine başlatılan hiçbir oluşturucu yok.  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Dikkat varsayılan değerini `age` olduğu `0` ve varsayılan değerini `name` olduğu `null`. Varsayılan değerleri hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Örnek 3  
 Aşağıdaki örnek, temel sınıf Başlatıcı kullanmayı gösterir. `Circle` Genel sınıfından türetilmiş sınıf `Shape`ve `Cylinder` sınıfı türetilen `Circle` sınıfı. Her bir türetilmiş sınıf oluşturucu, temel sınıf Başlatıcısı kullanıyor.  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Temel sınıf oluşturucuları Çağırma ile ilgili daha fazla örnek için bkz: [sanal](../../../csharp/language-reference/keywords/virtual.md), [geçersiz kılma](../../../csharp/language-reference/keywords/override.md), ve [temel](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [static](../../../csharp/language-reference/keywords/static.md)
