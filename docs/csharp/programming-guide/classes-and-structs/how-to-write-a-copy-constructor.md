---
title: Kopya oluşturucu nasıl yazılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714848"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Kopya oluşturucu nasıl yazılır (C# Programlama Kılavuzu)
C# nesneler için bir kopya oluşturucu sağlamaz, ancak kendiniz yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `Person` [sınıf,](../../language-reference/keywords/class.md) bağımsız değişkeni olarak `Person`bir kopyasını alan bir kopya oluşturucu tanımlar. Bağımsız değişkenin özelliklerinin değerleri yeni örneğin in özelliklerine `Person`atanır. Kod, kopyalamak istediğiniz örneğin `Name` özelliklerini `Age` ve özelliklerini sınıfın örnek oluşturucuya gönderen alternatif bir kopya oluşturucu içerir.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ICloneable>
- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
