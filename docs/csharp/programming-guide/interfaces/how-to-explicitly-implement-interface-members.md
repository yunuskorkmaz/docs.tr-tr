---
title: 'Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5f7ae6bae46cdf6596b206abbdeeb94b5c21a13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332192"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)
Bu örnek bildiren bir [arabirimi](../../../csharp/language-reference/keywords/interface.md), `IDimensions`ve sınıfı, bir `Box`, arabirim üyelerini açıkça uygulayan `getLength` ve `getWidth`. Üyeler arabirim örneğinin erişilen `dimensions`.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
-   Aşağıdaki satırları, içinde bildirim `Main` yöntemi, derleme hataları msgıd çünkü dışı bırakılır. Açıkça gerçekleştirilen bir arabirim üyesini gelen erişilemez bir [sınıfı](../../../csharp/language-reference/keywords/class.md) örneği:  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   Ayrıca, aşağıdaki satırları dikkat `Main` yöntemi, bir arabirim örneğinden yöntemleri adlı çünkü başarıyla yazdırma kutusunun boyutları:  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)  
 [Nasıl yapılır: İki Arabirimin Üyelerini Açıkça Uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
