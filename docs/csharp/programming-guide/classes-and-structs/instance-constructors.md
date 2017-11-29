---
title: "Örnek Oluşturucuları (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: efb82128ffc27a7c065d2ba12bfc08396d3b5cf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="instance-constructors-c-programming-guide"></a>Örnek Oluşturucuları (C# Programlama Kılavuzu)
Örnek oluşturucuları oluşturmak ve kullandığınızda herhangi bir örnek üye değişkeni başlatmak için kullanılan [yeni](../../../csharp/language-reference/keywords/new.md) bir nesne oluşturmak için ifade bir [sınıfı](../../../csharp/language-reference/keywords/class.md). Başlatmak için bir [statik](../../../csharp/language-reference/keywords/static.md) sınıfı ya da statik olmayan sınıftaki statik değişkenler statik Oluşturucu tanımlamanız gerekir. Daha fazla bilgi için bkz: [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 Aşağıdaki örnek, örnek oluşturucu gösterir:  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Daha anlaşılır olması için bu sınıf ortak alanları içerir. Genel alanlar kullanımını bir programı başka bir yerindeki herhangi bir yöntemini Kısıtlanmamış ve nesnenin çalışmalar erişimi doğrulanmamış izin verdiği için önerilen bir programlama uygulama değil. Veri üyeleri genellikle özel olmalıdır ve yalnızca sınıfı yöntemleri ve özellikleri erişilmelidir.  
  
 Bir nesne esas her Bu örnek oluşturucu çağrılır `CoOrds` sınıfı oluşturulur. Bağımsız değişken almayan, bunu adlı gibi bir oluşturucu bir *varsayılan oluşturucu*. Ancak, genellikle ek oluşturucular sağlamak yararlı olacaktır. Örneğin, bir oluşturucuya ekleyebiliriz `CoOrds` bize veri üyeleri için başlangıç değerlerini belirtmenizi sağlayan sınıfı:  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Böylece `CoOrd` varsayılan veya özel ilk değerleri ile oluşturulan nesnelere şöyle:  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Bir sınıf bir oluşturucuya sahip değilse, varsayılan bir oluşturucu otomatik olarak oluşturulur ve varsayılan değerler nesne alanları başlatmak için kullanılır. Örneğin, bir [int](../../../csharp/language-reference/keywords/int.md) 0 olarak başlatılır. Varsayılan değerleri hakkında daha fazla bilgi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). Bu nedenle, çünkü `CoOrds` sınıfı varsayılan oluşturucu, tüm veri üyeleri sıfırdan başlatır, sınıf nasıl çalıştığını değiştirmeden tamamen kaldırılabilir. Birden çok oluşturucuları kullanarak tam bir örnek daha sonra bu konudaki örnek 1'de sağlanan ve otomatik olarak oluşturulan bir oluşturucu örneği örnek 2'de sağlanır.  
  
 Örnek oluşturucuları, temel sınıflarının örnek oluşturucuları çağırmak için de kullanılabilir. Sınıf oluşturucu başlatıcı üzerinden temel sınıf gibi çağırabilirsiniz:  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 Bu örnekte, `Circle` sınıfı tarafından sağlanan oluşturucuya RADIUS ve yükseklik gösteren değerlerin geçirir `Shape` içinden `Circle` türetilir. Kullanarak bir tam örnek `Shape` ve `Circle` bu konudaki örnek 3 olarak görünür.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnek, iki sınıf oluşturucular ve bağımsız değişkenler olmadan bir iki bağımsız değişkeni ile bir sınıfı gösterir.  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Örnek 2  
 Bu örnekte, sınıf `Person` durumda, varsayılan bir oluşturucu otomatik olarak sağlanır ve alanları varsayılan değerlerine başlatılan tüm oluşturucular yok.  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Dikkat varsayılan değerini `age` olan `0` ve varsayılan değerini `name` olan `null`. Varsayılan değerleri hakkında daha fazla bilgi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Örnek 3  
 Aşağıdaki örnek, temel sınıf Başlatıcı kullanmayı gösterir. `Circle` Genel sınıfından türetilmiş sınıf `Shape`ve `Cylinder` sınıfı türetilir `Circle` sınıfı. Her türetilmiş sınıf oluşturucu, temel sınıf Başlatıcısı kullanıyor.  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Temel sınıf oluşturucular Çağırma ile ilgili daha fazla örnek için bkz: [sanal](../../../csharp/language-reference/keywords/virtual.md), [geçersiz kılma](../../../csharp/language-reference/keywords/override.md), ve [temel](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [statik](../../../csharp/language-reference/keywords/static.md)
