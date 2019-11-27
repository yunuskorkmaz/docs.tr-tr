---
title: Anonim Tür Tanımı
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: f8ac26577a7fbef865605a7ecf643fa733b2c2c0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344923"
---
# <a name="anonymous-type-definition-visual-basic"></a>Anonim Tür Tanımı (Visual Basic)

Anonim türdeki bir örneğin bildirimine yanıt olarak, derleyici tür için belirtilen özellikleri içeren yeni bir sınıf tanımı oluşturur.

## <a name="compiler-generated-code"></a>Derleyici tarafından üretilen kod

Aşağıdaki `product`tanımı için, derleyici `Name`, `Price`ve `OnHand`özellikleri içeren yeni bir sınıf tanımı oluşturur.

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

Sınıf tanımı aşağıdakine benzer özellik tanımları içerir. Anahtar özellikleri için `Set` yöntemi olmadığına dikkat edin. Anahtar özelliklerinin değerleri salt okunurdur.

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

Anonim bir tür bildiriminde en az bir anahtar özellik varsa, tür tanımı <xref:System.Object>devralınan üç üyeyi geçersiz kılar: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>ve <xref:System.Object.ToString%2A>. Hiçbir anahtar özellik bildirilmemiş ise, yalnızca <xref:System.Object.ToString%2A> geçersiz kılınır. Geçersiz kılmalar aşağıdaki işlevleri sağlar:

- `Equals`, iki anonim tür örneği aynı örnekle varsa veya aşağıdaki koşullara uyuyorsa `True` döndürür:

  - Aynı sayıda özelliği vardır.

  - Özellikler aynı sırada ve aynı ada ve aynı gösterilen türlerle birlikte bildirilmiştir. Ad karşılaştırmaları büyük/küçük harfe duyarlı değildir.

  - Özelliklerden en az biri bir anahtar özelliktir ve `Key` anahtar sözcüğü aynı özelliklere uygulanır.

  - Her bir karşılık gelen anahtar özellikleri çiftinin karşılaştırılması `True`döndürür.

    Örneğin, aşağıdaki örneklerde `Equals` yalnızca `employee01` ve `employee08`için `True` döndürür. Her satırdan önceki yorum, yeni örneğin `employee01`eşleşmemesi nedenini belirtir.

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- `GetHashcode` uygun bir benzersiz GetHashCode algoritması sağlar. Algoritma, karma kodu hesaplamak için yalnızca anahtar özelliklerini kullanır.

- `ToString`, aşağıdaki örnekte gösterildiği gibi, art arda eklenmiş özellik değerlerinin bir dizesini döndürür. Anahtar ve anahtar olmayan özellikler dahil edilmiştir.

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

Anonim bir türün açıkça adlandırılmış özellikleri, oluşturulan bu yöntemlerle çakışamaz. Diğer bir deyişle, bir özelliği adlandırmak için `.Equals`, `.GetHashCode`veya `.ToString` kullanamazsınız.

En az bir anahtar özelliği içeren anonim tür tanımları <xref:System.IEquatable%601?displayProperty=nameWithType> arabirimini de uygular; burada `T` anonim türün türüdür.

> [!NOTE]
> Anonim tür bildirimleri aynı anonim türü yalnızca aynı derlemede gerçekleştiklerinde oluşturduklarında, özellikleri aynı ada ve aynı gösterilen türlere sahiptir, özellikler aynı sırada ve aynı Özellikler anahtar özellikleri olarak işaretlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Anonim Tipler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Nasıl yapılır: Anonim Tip Bildirimlerinden Özellik Adları ve Türlerini Çıkarma](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
