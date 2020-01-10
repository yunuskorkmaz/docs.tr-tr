---
title: Kopya Oluşturucu yazma- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714848"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Kopya Oluşturucu yazma (C# Programlama Kılavuzu)
C#nesneler için bir kopya Oluşturucu sağlamaz, ancak kendiniz bir tane yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Person`[sınıfı](../../language-reference/keywords/class.md) , bir `Person`örneği olan bağımsız değişkeni olarak alan bir kopya Oluşturucu tanımlar. Bağımsız değişkeninin özelliklerinin değerleri `Person`yeni örneğinin özelliklerine atanır. Kod, sınıfının örnek oluşturucusuna kopyalamak istediğiniz örneğin `Name` ve `Age` özelliklerini gönderen alternatif bir kopya Oluşturucu içerir.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ICloneable>
- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
