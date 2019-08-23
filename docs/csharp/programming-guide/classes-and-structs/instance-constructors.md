---
title: Örnek oluşturucular- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 198f9db1430226343fd3709c66d16b68e975ab3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922164"
---
# <a name="instance-constructors-c-programming-guide"></a>Örnek Oluşturucuları (C# Programlama Kılavuzu)

Örnek oluşturucular, bir [sınıfın](../../language-reference/keywords/class.md)nesnesini oluşturmak için [Yeni](../../language-reference/operators/new-operator.md) ifadeyi kullandığınızda herhangi bir örnek üye değişkeni oluşturmak ve başlatmak için kullanılır. Statik bir sınıf [](../../language-reference/keywords/static.md) veya statik değişkenleri statik olmayan bir sınıfta başlatmak için statik bir Oluşturucu tanımlarsınız. Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).  
  
 Aşağıdaki örnek bir örnek Oluşturucu göstermektedir:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> Açıklık için, bu sınıf ortak alanlar içerir. Ortak alanların kullanımı önerilen bir programlama uygulaması değildir çünkü bir programda herhangi bir yerde herhangi bir yerdeki herhangi bir yönteme izin verir ve bir nesnenin iç işleyişi için doğrulanmamış erişimdir. Veri üyeleri genellikle özel olmalıdır ve yalnızca sınıf yöntemleri ve özellikleri aracılığıyla erişilmelidir.  
  
 Bu örnek Oluşturucu, `Coords` sınıfı temel alan bir nesne oluşturulduğunda çağrılır. Böyle bir bağımsız değişken alan bir Oluşturucu gibi bir oluşturucuya *parametresiz Oluşturucu*denir. Ancak, genellikle ek oluşturucular sağlamak yararlı olur. Örneğin, `Coords` sınıfa veri üyeleri için başlangıç değerlerini belirtmemizi sağlayan bir Oluşturucu ekleyebiliriz:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 Bu, `Coords` nesnelerin varsayılan veya belirli başlangıç değerleriyle oluşturulmasına izin verir, örneğin:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Bir sınıfın Oluşturucusu yoksa, parametresiz bir Oluşturucu otomatik olarak oluşturulur ve nesne alanlarını başlatmak için varsayılan değerler kullanılır. Örneğin, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 0 olarak başlatılır. Varsayılan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../language-reference/keywords/default-values-table.md). Bu nedenle, `Coords` parametresiz bir Oluşturucu tüm veri üyelerini sıfıra başlattığında, sınıfın çalışma biçimini değiştirmeden tamamen kaldırılabilir. Bu konunun ilerleyen kısımlarında örnek 1 ' de birden çok Oluşturucu kullanan bir örnek verilmiştir ve örnek 2 ' de otomatik olarak oluşturulan bir oluşturucuya örnek verilmiştir.  
  
 Örnek oluşturucular, temel sınıfların örnek oluşturucularını çağırmak için de kullanılabilir. Sınıf oluşturucusu, aşağıdaki gibi, başlatıcı aracılığıyla temel sınıfın oluşturucusunu çağırabilir:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 Bu örnekte, `Circle` sınıfı, RADIUS ve yüksekliği temsil eden değerleri, öğesinden `Circle` türetilmiş tarafından `Shape` sunulan oluşturucuya geçirir. `Shape` Ve`Circle` bu konuda örnek 3 olarak görünen bir örnek.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnek, bağımsız değişkenler olmadan biri ve iki bağımsız değişken içeren iki sınıf oluşturucusuna sahip bir sınıfı gösterir.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Örnek 2  
 Bu örnekte, sınıfın `Person` herhangi bir Oluşturucusu yoktur, bu durumda parametresiz bir Oluşturucu otomatik olarak sağlanır ve alanlar varsayılan değerlerine başlatılır.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 `age` Varsayılan değerinin `0` vevarsayılan`null`değerinin olduğunu unutmayın. `name` Varsayılan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Örnek 3  
 Aşağıdaki örnek, temel sınıf başlatıcısının kullanımını gösterir. Sınıfı genel sınıftan `Shape`türetilir ve `Cylinder` sınıfı `Circle` sınıfından türetilir. `Circle` Türetilmiş her sınıftaki Oluşturucu kendi temel sınıf başlatıcısını kullanıyor.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Temel sınıf oluşturucularını çağırma hakkında daha fazla örnek için bkz. [sanal](../../language-reference/keywords/virtual.md), [geçersiz kılma](../../language-reference/keywords/override.md)ve [temel](../../language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
- [static](../../language-reference/keywords/static.md)
