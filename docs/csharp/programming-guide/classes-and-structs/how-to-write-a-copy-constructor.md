---
title: 'Nasıl yapılır: Kopya Oluşturucu Yazma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 8a7cc85d40272918f4839d13fcccb79b558eeac7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Nasıl yapılır: Kopya Oluşturucu Yazma (C# Programlama Kılavuzu)
C# kopya Oluşturucu nesneler için sağlamaz, ancak kendiniz yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Person` [sınıfı](../../../csharp/language-reference/keywords/class.md) alır, bir kopya oluşturucu bağımsız değişken olarak, bir örneğini tanımlar `Person`. Bağımsız değişken özelliklerinin değerleri yeni bir örneğini özelliklerine atanan `Person`. Gönderen bir alternatif kopya Oluşturucu kodu içeren `Name` ve `Age` sınıfının örneği oluşturucusu kopyalamak istediğiniz örneğinin özelliklerini.  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ICloneable>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
