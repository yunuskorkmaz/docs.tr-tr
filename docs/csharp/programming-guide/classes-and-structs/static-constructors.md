---
title: "Statik Oluşturucular (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee5448095cf06c2473c94bae542c02557918271a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="static-constructors-c-programming-guide"></a>Statik Oluşturucular (C# Programlama Kılavuzu)
Statik Oluşturucu herhangi başlatmak için kullanılan [statik](../../../csharp/language-reference/keywords/static.md) verileri, yalnızca bir kez gerçekleştirilmesi gerekir belirli bir eylemi gerçekleştirmek için veya. Otomatik olarak ilk örneği oluşturulduğunda veya herhangi bir statik üye başvurulan önce çağrılır.  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Statik oluşturucular aşağıdaki özelliklere sahiptir:  
  
-   Statik Oluşturucu erişim değiştiricileri alın ya da parametrelere sahip.  
  
-   Statik Oluşturucu otomatik olarak başlatmak için çağrılır [sınıfı](../../../csharp/language-reference/keywords/class.md) ilk örneği oluşturulduğunda veya herhangi bir statik üye başvurulan önce.  
  
-   Statik Oluşturucu doğrudan çağrılamaz.  
  
-   Kullanıcının statik Oluşturucusu programa zaman yürütülür üzerinde denetimi yoktur.  
  
-   Statik Oluşturucular, tipik kullanımını sınıfı bir günlük dosyası kullanıyor ve Oluşturucusu girişler bu dosyaya yazmak için kullanılan durumdur.  
  
-   Statik oluşturucular de yararlı Oluşturucusu çağırabilirsiniz yönetilmeyen kod için sarmalayıcı sınıflar oluştururken `LoadLibrary` yöntemi.  
  
-   Statik Oluşturucusu bir özel durum oluşturursa, çalışma zamanı, ikinci kez çağırmayacaktır ve türü programınızı çalıştığı uygulama etki alanı için kullanım ömrünü başlatılmamış kalır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, sınıf `Bus` statik bir oluşturucuya sahip. Zaman ilk örneğini `Bus` oluşturulur (`bus1`), statik Oluşturucusu sınıfını başlatmak için çağrılır. Örnek çıktı statik oluşturucusunu yalnızca bir kez rağmen iki örneğini çalıştığını doğrular `Bus` oluşturulur ve örnek oluşturucu döngülerinden önce çalışır.  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
