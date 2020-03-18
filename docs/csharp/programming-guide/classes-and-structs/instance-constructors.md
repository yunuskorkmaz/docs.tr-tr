---
title: Örnek Oluşturucular - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964722"
---
# <a name="instance-constructors-c-programming-guide"></a>Örnek Oluşturucuları (C# Programlama Kılavuzu)

Örnek oluşturucular, bir [sınıfın](../../language-reference/keywords/class.md)nesnesini oluşturmak için [yeni](../../language-reference/operators/new-operator.md) ifadeyi kullandığınızda herhangi bir örnek üye değişken oluşturmak ve başlatmak için kullanılır. [Statik](../../language-reference/keywords/static.md) olmayan bir sınıfta statik bir sınıf veya statik değişkenler başlatma, statik bir oluşturucu tanımlarsınız. Daha fazla bilgi için Statik [Oluşturucular'a](./static-constructors.md)bakın.  
  
 Aşağıdaki örnek oluşturucu bir örneği gösterir:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> Açıklık için, bu sınıf ortak alanları içerir. Ortak alanların kullanımı, bir programın herhangi bir yerindeki herhangi bir yöntemin nesnenin iç işleyişine sınırsız ve doğrulanmamış erişime izin verdiği için önerilen bir programlama uygulaması değildir. Veri üyeleri genellikle özel olmalı ve yalnızca sınıf yöntemleri ve özellikleri ile erişilmelidir.  
  
 Bu örnek `Coords` oluşturucu, sınıfa dayalı bir nesne oluşturulduğunda çağrılır. Bunun gibi hiçbir bağımsız değişken alan bir yapıcıya *parametresiz yapıcı*denir. Ancak, genellikle ek oluşturucular sağlamak yararlıdır. Örneğin, `Coords` sınıfa veri üyeleri için başlangıç değerlerini belirtmemizi sağlayan bir oluşturucu ekleyebiliriz:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 Bu, `Coords` nesnelerin varsayılan veya belirli başlangıç değerleri yle oluşturulmasına izin verir:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Bir sınıfın oluşturucusu yoksa, parametresiz bir oluşturucu otomatik olarak oluşturulur ve nesne alanlarını başlatmak için varsayılan değerler kullanılır. Örneğin, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 0'a başharfle başlanır. Tür varsayılan değerleri hakkında bilgi için [C# türlerinin Varsayılan değerlerine](../../language-reference/builtin-types/default-values.md)bakın. Bu nedenle, `Coords` sınıf parametresiz oluşturucu tüm veri üyelerini sıfıra indirdiği için, sınıfın çalışma şeklini değiştirmeden tamamen kaldırılabilir. Bu konunun ilerleyen saatlerinde Örnek 1'de birden çok oluşturucu kullanılarak tam bir örnek verilmiştir ve Örnek 2'de otomatik olarak oluşturulan bir oluşturucu örneği verilmiştir.  
  
 Örnek oluşturucular, taban sınıfların örnek oluşturucularını çağırmak için de kullanılabilir. Sınıf oluşturucu, taban sınıfın oluşturucusu başlatıcısı aracılığıyla aşağıdaki gibi çağırabilir:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 Bu örnekte, `Circle` sınıf yarıçapı ve yüksekliği temsil eden `Shape` değerleri `Circle` türetildiği tarafından sağlanan oluşturucuya geçirir. Tam bir `Shape` örnek `Circle` kullanarak ve örnek 3 olarak bu konu görünür.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıdaki örnek, biri bağımsız, diğeri iki bağımsız değişkenli olmak üzere iki sınıf oluşturucusu olan bir sınıfı gösterir.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Örnek 2  
 Bu örnekte, `Person` sınıfın herhangi bir oluşturucusu yoktur, bu durumda parametresiz bir oluşturucu otomatik olarak sağlanır ve alanlar varsayılan değerlerine başolarak başlar.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Varsayılan değerin `age` ve `0` varsayılan değerinin `name` . `null`
  
## <a name="example-3"></a>Örnek 3  
 Aşağıdaki örnek, taban sınıf baş harflerini kullanarak gösteriş gösterir. Sınıf `Circle` genel sınıftan `Shape`türetilir `Cylinder` ve sınıf `Circle` sınıftan türetilir. Her türemiş sınıfın oluşturucusu taban sınıf baş harflerini kullanıyor.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Taban sınıf oluşturucuları çağırmak la ilgili daha fazla örnek için [sanal,](../../language-reference/keywords/virtual.md) [geçersiz kılma](../../language-reference/keywords/override.md)ve [taban'a](../../language-reference/keywords/base.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
- [Statik](../../language-reference/keywords/static.md)
