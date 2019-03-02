---
title: Örnek oluşturucuları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: c698ffc8d1bc68b2ebcbdf4578ab5926d4743516
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203476"
---
# <a name="instance-constructors-c-programming-guide"></a>Örnek Oluşturucuları (C# Programlama Kılavuzu)
Örnek oluşturucuları oluşturup kullandığınızda tüm örnek üye değişkenlerini başlatmak için kullanılan [yeni](../../../csharp/language-reference/keywords/new.md) ifade bir nesne oluşturmak için bir [sınıfı](../../../csharp/language-reference/keywords/class.md). Başlatmak için bir [statik](../../../csharp/language-reference/keywords/static.md) sınıf veya bir statik olmayan sınıf içinde statik değişkenler bir statik Oluşturucu tanımlamanız gerekir. Daha fazla bilgi için [statik oluşturucular](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 Aşağıdaki örnek, bir örnek oluşturucusunda gösterir:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
>  Anlaşılsın diye, bu sınıf, ortak alanları içerir. Bir programda herhangi bir yerde herhangi bir yöntemi Kısıtlanmamış ve doğrulanmamış bir nesnenin iç çalışmalarına değineceğiz erişimi verdiğinden, ortak alanları kullanımını önerilen bir programlama uygulama değil. Veri üyeleri, genellikle özel olmalıdır ve yalnızca sınıfı yöntemleri ve özellikleri erişilmelidir.  
  
 Bir nesne dayalı olduğunda, bu örneği Oluşturucu çağrılır `Coords` sınıf oluşturulur. Hiçbir bağımsız değişkeni alır, bu bir adlı gibi bir oluşturucu bir *varsayılan oluşturucu*. Ancak, genellikle ek oluşturucular sağlamak için yararlı olur. Örneğin, bir oluşturucuya ekleyebiliriz `Coords` veri üyeleri için başlangıç değerlerini belirtmek sağlıyor sınıfı:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 Böylece `Coords` varsayılan veya özel ilk değerleri ile oluşturulan nesnelere şöyle:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Bir sınıf bir oluşturucu yoksa, bir varsayılan oluşturucu otomatik olarak oluşturulur ve varsayılan değerler nesne alanları başlatmak için kullanılır. Örneğin, bir [int](../../../csharp/language-reference/keywords/int.md) 0 olarak başlatılır. Varsayılan değerleri hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md). Bu nedenle, çünkü `Coords` sınıf varsayılan oluşturucusuna tüm veri üyeleri sıfırdan başlatır, sınıf şeklini değiştirmeden tamamen kaldırılabilir. Birden çok oluşturucuları kullanarak tam bir örnek daha sonra bu konudaki örnek 1'de sağlanan ve otomatik olarak oluşturulan bir oluşturucu örneği örnek 2'de sağlanır.  
  
 Örnek oluşturucuları, temel sınıfların örnek oluşturucuları çağırmak için de kullanılabilir. Sınıf oluşturucu başlatıcı aracılığıyla temel sınıfın Oluşturucusu gibi çağırabilirsiniz:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 Bu örnekte, `Circle` sınıfı tarafından sağlanan oluşturucusu için RADIUS ve yüksekliğini temsil eden değerleri geçirir `Shape` içinden `Circle` türetilir. Kullanarak bir tam örnek `Shape` ve `Circle` bu konudaki örnek 3 olarak görünür.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnek, iki sınıf oluşturucuları, bir bağımsız değişkenler olmadan ve iki bağımsız değişkeni ile tek bir sınıfı gösterir.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Örnek 2  
 Bu örnekte, sınıf `Person` durumda bir varsayılan oluşturucu otomatik olarak sağlanır ve alanları varsayılan değerlerine başlatılan hiçbir oluşturucu yok.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Dikkat varsayılan değerini `age` olduğu `0` ve varsayılan değerini `name` olduğu `null`. Varsayılan değerleri hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Örnek 3  
 Aşağıdaki örnek, temel sınıf Başlatıcı kullanmayı gösterir. `Circle` Genel sınıfından türetilmiş sınıf `Shape`ve `Cylinder` sınıfı türetilen `Circle` sınıfı. Her bir türetilmiş sınıf oluşturucu, temel sınıf Başlatıcısı kullanıyor.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Temel sınıf oluşturucuları Çağırma ile ilgili daha fazla örnek için bkz: [sanal](../../../csharp/language-reference/keywords/virtual.md), [geçersiz kılma](../../../csharp/language-reference/keywords/override.md), ve [temel](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [static](../../../csharp/language-reference/keywords/static.md)
