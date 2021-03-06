---
title: Kopya Oluşturucu yazma-C# Programlama Kılavuzu
description: Sınıfının bir örneğini alan ve girişin değerleriyle yeni bir örnek döndüren C# ' de bir kopya Oluşturucu yazmayı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: c61018444dd600d6f33765b104034355d0301667
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255242"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Kopya Oluşturucu yazma (C# Programlama Kılavuzu)

C# [kayıtları](records.md) nesneler için bir kopya Oluşturucusu sağlar, ancak sınıflar için kendiniz yazmanız gerekir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte `Person` [sınıfı](../../language-reference/keywords/class.md) , bir örneği olan bağımsız değişkeni olarak alan bir kopya Oluşturucu tanımlar `Person` . Bağımsız değişkeninin özelliklerinin değerleri, yeni örneğinin özelliklerine atanır `Person` . Kod, `Name` `Age` sınıfının örnek oluşturucusuna kopyalamak istediğiniz örneğin ve özelliklerini gönderen alternatif bir kopya Oluşturucu içerir.  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ICloneable>
- [Kayıtlar](records.md)
- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
