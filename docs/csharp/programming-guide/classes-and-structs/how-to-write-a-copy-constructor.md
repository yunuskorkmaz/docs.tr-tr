---
title: 'Nasıl yapılır: Kopya Oluşturucu Yazma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: d6ecfc3659dcf533db0f4e7b67fdffd620a584fd
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323005"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Nasıl yapılır: Kopya Oluşturucu Yazma (C# Programlama Kılavuzu)
C# nesneler için bir kopya Oluşturucusu sağlamaz, ancak kendiniz bir tane yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Person` [sınıfı](../../../csharp/language-reference/keywords/class.md) alan, bir kopya oluşturucu bağımsız değişken olarak, bir örneğini tanımlar `Person`. Bağımsız değişken özelliklerinin değerleri, yeni bir örneğini özelliklerine atanan `Person`. Gönderen bir alternatif bir kopya Oluşturucu kodunu içeren `Name` ve `Age` sınıfın örnek oluşturucusuna kopyalamak istediğiniz örneğin özellikleri.  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.ICloneable>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
