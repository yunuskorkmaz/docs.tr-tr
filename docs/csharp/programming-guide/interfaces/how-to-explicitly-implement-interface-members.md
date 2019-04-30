---
title: 'Nasıl yapılır: -Arabirim üyelerini açıkça uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: d5630065ae1fbfceca9ce3b5180664bba3a104a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710270"
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
