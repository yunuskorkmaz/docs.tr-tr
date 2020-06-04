---
title: Anonim Tip Tanımı
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 952eb295cc71eab5d0ad6e18f2b697a9b701b434
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404907"
---
# <a name="anonymous-type-definition-visual-basic"></a>Anonim Tür Tanımı (Visual Basic)

Anonim türdeki bir örneğin bildirimine yanıt olarak, derleyici tür için belirtilen özellikleri içeren yeni bir sınıf tanımı oluşturur.

## <a name="compiler-generated-code"></a>Derleyici tarafından üretilen kod

Aşağıdaki tanımı için, `product` derleyici, ve özelliklerini içeren yeni bir sınıf tanımı oluşturur `Name` `Price` `OnHand` .

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

Sınıf tanımı aşağıdakine benzer özellik tanımları içerir. `Set`Anahtar özellikleri için bir yöntem olmadığına dikkat edin. Anahtar özelliklerinin değerleri salt okunurdur.

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

Buna ek olarak, anonim tür tanımları parametresiz bir Oluşturucu içerir. Parametre gerektiren oluşturuculara izin verilmez.

Anonim bir tür bildiriminde en az bir anahtar özellik varsa tür tanımı, öğesinden devralınan üç üyeyi geçersiz kılar <xref:System.Object> : <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> , ve <xref:System.Object.ToString%2A> . Hiçbir anahtar özellik bildirilmemiş ise, yalnızca <xref:System.Object.ToString%2A> geçersiz kılınır. Geçersiz kılmalar aşağıdaki işlevleri sağlar:

- `Equals``True`iki anonim tür örneği aynı örnekle ise veya aşağıdaki koşullara uyuyorsa döndürür:

  - Aynı sayıda özelliği vardır.

  - Özellikler aynı sırada ve aynı ada ve aynı gösterilen türlerle birlikte bildirilmiştir. Ad karşılaştırmaları büyük/küçük harfe duyarlı değildir.

  - Özelliklerden en az biri bir anahtar özelliktir ve `Key` anahtar sözcüğü aynı özelliklere uygulanır.

  - Her bir karşılık gelen anahtar özellikleri çiftinin karşılaştırması döndürür `True` .

    Örneğin, aşağıdaki örneklerde `Equals` `True` yalnızca ve için döndürür `employee01` `employee08` . Her satırdan önceki yorum, yeni örneğin eşleşmemesinin nedenini belirtir `employee01` .

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode`uygun şekilde benzersiz bir GetHashCode algoritması sağlar. Algoritma, karma kodu hesaplamak için yalnızca anahtar özelliklerini kullanır.

- `ToString`Aşağıdaki örnekte gösterildiği gibi, art arda eklenmiş özellik değerleri dizesini döndürür. Anahtar ve anahtar olmayan özellikler dahil edilmiştir.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Anonim bir türün açıkça adlandırılmış özellikleri, oluşturulan bu yöntemlerle çakışamaz. Diğer bir deyişle,,, `.Equals` `.GetHashCode` veya özelliğini kullanamazsınız `.ToString` .

En az bir anahtar özelliği içeren anonim tür tanımları arabirimini de uygular <xref:System.IEquatable%601?displayProperty=nameWithType> , burada `T` anonim türün türüdür.

> [!NOTE]
> Anonim tür bildirimleri aynı anonim türü yalnızca aynı derlemede gerçekleştiklerinde oluşturduklarında, özellikleri aynı ada ve aynı gösterilen türlere sahiptir, özellikler aynı sırada ve aynı Özellikler anahtar özellikleri olarak işaretlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Anonim Türler](anonymous-types.md)
- [Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
