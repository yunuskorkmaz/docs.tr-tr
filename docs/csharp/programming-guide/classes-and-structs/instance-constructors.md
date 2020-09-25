---
title: Örnek oluşturucular-C# Programlama Kılavuzu
description: C# ' deki örnek oluşturucular, bir sınıfın nesnesini oluşturmak için yeni ifadeyi kullandığınızda herhangi bir örnek üye değişkenlerini oluşturur ve başlatır.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: f1845601f2a0237206d05e3cc3cbbca68492020c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186139"
---
# <a name="instance-constructors-c-programming-guide"></a>Örnek Oluşturucuları (C# Programlama Kılavuzu)

Örnek oluşturucular, bir [sınıfın](../../language-reference/keywords/class.md)nesnesini oluşturmak için [Yeni](../../language-reference/operators/new-operator.md) ifadeyi kullandığınızda herhangi bir örnek üye değişkeni oluşturmak ve başlatmak için kullanılır. Statik [bir sınıf veya](../../language-reference/keywords/static.md) statik değişkenleri statik olmayan bir sınıfta başlatmak için statik bir Oluşturucu tanımlarsınız. Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).  
  
 Aşağıdaki örnek bir örnek Oluşturucu göstermektedir:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> Açıklık için, bu sınıf ortak alanlar içerir. Ortak alanların kullanımı önerilen bir programlama uygulaması değildir çünkü bir programda herhangi bir yerde herhangi bir yerdeki herhangi bir yönteme izin verir ve bir nesnenin iç işleyişi için doğrulanmamış erişimdir. Veri üyeleri genellikle özel olmalıdır ve yalnızca sınıf yöntemleri ve özellikleri aracılığıyla erişilmelidir.  
  
 Bu örnek Oluşturucu, sınıfı temel alan bir nesne oluşturulduğunda çağrılır `Coords` . Böyle bir bağımsız değişken alan bir Oluşturucu gibi bir oluşturucuya *parametresiz Oluşturucu*denir. Ancak, genellikle ek oluşturucular sağlamak yararlı olur. Örneğin, `Coords` sınıfa veri üyeleri için başlangıç değerlerini belirtmemizi sağlayan bir Oluşturucu ekleyebiliriz:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 Bu `Coords` , nesnelerin varsayılan veya belirli başlangıç değerleriyle oluşturulmasına izin verir, örneğin:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 Bir sınıfın Oluşturucusu yoksa, parametresiz bir Oluşturucu otomatik olarak oluşturulur ve nesne alanlarını başlatmak için varsayılan değerler kullanılır. Örneğin, bir [int](../../language-reference/builtin-types/integral-numeric-types.md) 0 olarak başlatılır. Tür varsayılan değerleri hakkında daha fazla bilgi için bkz. [C# türlerin varsayılan değerleri](../../language-reference/builtin-types/default-values.md). Bu nedenle, `Coords` parametresiz bir Oluşturucu tüm veri üyelerini sıfıra başlattığında, sınıfın çalışma biçimini değiştirmeden tamamen kaldırılabilir. Bu konunun ilerleyen kısımlarında örnek 1 ' de birden çok Oluşturucu kullanan bir örnek verilmiştir ve örnek 2 ' de otomatik olarak oluşturulan bir oluşturucuya örnek verilmiştir.  
  
 Örnek oluşturucular, temel sınıfların örnek oluşturucularını çağırmak için de kullanılabilir. Sınıf oluşturucusu, aşağıdaki gibi, başlatıcı aracılığıyla temel sınıfın oluşturucusunu çağırabilir:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 Bu örnekte, sınıfı, `Circle` RADIUS ve yüksekliği temsil eden değerleri, öğesinden türetilmiş tarafından sunulan oluşturucuya geçirir `Shape` `Circle` . `Shape`Ve `Circle` Bu konuda örnek 3 olarak görünen bir örnek.  
  
## <a name="example-1"></a>Örnek 1  

 Aşağıdaki örnek, bağımsız değişkenler olmadan biri ve iki bağımsız değişken içeren iki sınıf oluşturucusuna sahip bir sınıfı gösterir.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a>Örnek 2  

 Bu örnekte, sınıfın `Person` herhangi bir Oluşturucusu yoktur, bu durumda parametresiz bir Oluşturucu otomatik olarak sağlanır ve alanlar varsayılan değerlerine başlatılır.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Varsayılan değerinin ve varsayılan değerinin olduğunu `age` unutmayın `0` `name` `null` .
  
## <a name="example-3"></a>Örnek 3  

 Aşağıdaki örnek, temel sınıf başlatıcısının kullanımını gösterir. `Circle`Sınıfı genel sınıftan türetilir `Shape` ve sınıfı `Cylinder` `Circle` sınıfından türetilir. Türetilmiş her sınıftaki Oluşturucu kendi temel sınıf başlatıcısını kullanıyor.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 Temel sınıf oluşturucularını çağırma hakkında daha fazla örnek için bkz. [sanal](../../language-reference/keywords/virtual.md), [geçersiz kılma](../../language-reference/keywords/override.md)ve [temel](../../language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
- [static](../../language-reference/keywords/static.md)
