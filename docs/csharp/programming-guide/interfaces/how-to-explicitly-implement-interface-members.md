---
title: "Nasıl yapılır: Arabirim Üyelerini Açıkça Uygulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e02ae26000057e4e7323a777a6a0e1ca6fd8871b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Arabirimleri](../../../csharp/programming-guide/interfaces/index.md)  
 [Nasıl yapılır: iki arabirimin üyelerini açıkça uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
