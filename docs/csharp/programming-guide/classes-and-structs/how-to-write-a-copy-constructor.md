---
title: 'Nasıl yapılır: Kopya Oluşturucu yazma- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: bdc352566052f4cec1686176131e9b1e1b768794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596609"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Nasıl yapılır: Kopya Oluşturucu yazma (C# Programlama Kılavuzu)
C#nesneler için bir kopya Oluşturucu sağlamaz, ancak kendiniz bir tane yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Person` [sınıfı](../../language-reference/keywords/class.md) , bir örneği `Person`olan bağımsız değişkeni olarak alan bir kopya Oluşturucu tanımlar. Bağımsız değişkeninin özelliklerinin değerleri, yeni örneğinin `Person`özelliklerine atanır. Kod, sınıfının örnek oluşturucusuna kopyalamak istediğiniz örneğin `Name` ve `Age` özelliklerini gönderen alternatif bir kopya Oluşturucu içerir.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ICloneable>
- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
