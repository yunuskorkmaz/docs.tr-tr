---
title: 'Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 30ea58b7ef3edd757c450b9fca1cc810ff9d17c1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861029"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)
Bu örnek bildirir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md), `IDimensions`ve bir sınıf, `Box`, arabirim üyelerini açıkça uygulayan `getLength` ve `getWidth`. Üye arabirim örneğinin erişilen `dimensions`.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
-   Aşağıdaki satırları, buna dikkat edin `Main` yöntemi, derleme hataya neden çünkü derleme dışı bırakılır. Açıkça uygulanan bir arabirim üyesi erişilemez bir [sınıfı](../../../csharp/language-reference/keywords/class.md) örneği:  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   Ayrıca, aşağıdaki satırları dikkat `Main` yöntem, yöntem bir arabirim örneğinden çağrılmadığından başarıyla yazdırma kutusunun boyutları:  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)  
- [Nasıl yapılır: İki Arabirimin Üyelerini Açıkça Uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
