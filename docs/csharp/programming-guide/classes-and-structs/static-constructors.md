---
title: Statik Oluşturucular (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 22be72547e96c66df3be115dac30a16559b23659
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502774"
---
# <a name="static-constructors-c-programming-guide"></a>Statik Oluşturucular (C# Programlama Kılavuzu)
Statik Oluşturucu herhangi başlatmak için kullanılan [statik](../../../csharp/language-reference/keywords/static.md) verileri veya yalnızca bir kez gerçekleştirilmesi gereken belirli bir eylemi gerçekleştirmek için. İlk örneği oluşturulduğunda veya herhangi bir statik üye başvurulan önce otomatik olarak adlandırılır.  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Statik Oluşturucular, aşağıdaki özelliklere sahiptir:  
  
-   Statik Oluşturucu erişim değiştiricileri alın veya parametreleri desteklemez.  
  
-   Statik Oluşturucu otomatik olarak başlatmak için çağırılır [sınıfı](../../../csharp/language-reference/keywords/class.md) önce ilk örneği oluşturulduğunda veya herhangi bir statik üye başvurulur.  
  
-   Statik Oluşturucu doğrudan çağrılamaz.  
  
-   Kullanıcının statik Oluşturucu programa ne zaman çalıştırılır üzerinde denetimi yoktur.  
  
-   Tipik bir kullanımı statik Oluşturucular, sınıf, bir günlük dosyası kullanarak ve oluşturucu girişleri bu dosyaya yazmak için kullanılan andır.  
  
-   Statik oluşturucular da yararlı Oluşturucu çağırabilir, yönetilmeyen kod için sarmalayıcı sınıflar oluşturma `LoadLibrary` yöntemi.  
  
-   Statik Oluşturucu bir özel durum oluşturursa, çalışma zamanı, ikinci kez çağırmayacaktır ve türü, programınızın çalıştığı uygulama etki alanı ömrü boyunca başlatılmamış kalır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıf `Bus` bir statik Oluşturucusu vardır. Zaman ilk örneğinin `Bus` oluşturulur (`bus1`), sınıf için statik Oluşturucu çağrılır. Statik Oluşturucu yalnızca bir kez olsa bile iki örneği çalıştığından örnek çıktısı doğrular `Bus` oluşturulur, ve örnek oluşturucu döngülerinden önce çalışır.  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
