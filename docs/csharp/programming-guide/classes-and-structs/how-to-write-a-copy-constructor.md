---
title: Kopya Oluşturucu yazma-C# Programlama Kılavuzu
description: Sınıfının bir örneğini alan ve girişin değerleriyle yeni bir örnek döndüren C# ' de bir kopya Oluşturucu yazmayı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: beb2fcfaa36303eeaabd5278cf5e7a128282270e
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864234"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Kopya Oluşturucu yazma (C# Programlama Kılavuzu)
C# nesneler için bir kopya Oluşturucu sağlamaz, ancak kendiniz bir tane yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Person` [sınıfı](../../language-reference/keywords/class.md) , bir örneği olan bağımsız değişkeni olarak alan bir kopya Oluşturucu tanımlar `Person` . Bağımsız değişkeninin özelliklerinin değerleri, yeni örneğinin özelliklerine atanır `Person` . Kod, `Name` `Age` sınıfının örnek oluşturucusuna kopyalamak istediğiniz örneğin ve özelliklerini gönderen alternatif bir kopya Oluşturucu içerir.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ICloneable>
- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
