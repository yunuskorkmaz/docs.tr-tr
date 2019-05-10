---
title: 'Nasıl yapılır: -Arabirim üyelerini açıkça uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 8cef6c840bf6afff8ccbf7d02012990e11d47991
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595366"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Nasıl yapılır: Arabirim üyelerini açıkça uygulama (C# Programlama Kılavuzu)
Bu örnek bildirir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md), `IDimensions`ve bir sınıf, `Box`, arabirim üyelerini açıkça uygulayan `getLength` ve `getWidth`. Üye arabirim örneğinin erişilen `dimensions`.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
- Aşağıdaki satırları, buna dikkat edin `Main` yöntemi, derleme hataya neden çünkü derleme dışı bırakılır. Açıkça uygulanan bir arabirim üyesi erişilemez bir [sınıfı](../../../csharp/language-reference/keywords/class.md) örneği:  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Ayrıca, aşağıdaki satırları dikkat `Main` yöntem, yöntem bir arabirim örneğinden çağrılmadığından başarıyla yazdırma kutusunun boyutları:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)
- [Nasıl yapılır: İki arabirimin üyelerini açıkça uygulama](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
