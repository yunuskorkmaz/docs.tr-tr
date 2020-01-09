---
title: 'Nasıl yapılır: dize içinde arama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 655f746e4e496e1935afcd2a9f9fe36d9e3a2564
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348417"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Nasıl yapılır: dize içinde arama (Visual Basic)

Bu makalede, Visual Basic bir dize içinde aramanın nasıl yapılacağı hakkında bir örnek gösterilmektedir.

## <a name="example"></a>Örnek

Bu örnek, bir alt dizenin ilk geçtiği dizini raporlamak için bir <xref:System.String> nesnesindeki <xref:System.String.IndexOf%2A> yöntemini çağırır:

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>Güçlü programlama

<xref:System.String.IndexOf%2A> yöntemi, alt dizenin ilk oluşumunun ilk karakterinin konumunu döndürür. Dizin 0 tabanlıdır, yani bir dizenin ilk karakterinin 0 dizinine sahip olduğu anlamına gelir.

<xref:System.String.IndexOf%2A> alt dizeyi bulamazsa,-1 döndürür.

<xref:System.String.IndexOf%2A> yöntemi, büyük/küçük harfe duyarlıdır ve geçerli kültürü kullanır.

En iyi hata denetimi için, bir TRY `Try` bloğunda dize aramasını kapsamak isteyebilirsiniz [... Yakala... Finally deyiminin](../../../language-reference/statements/try-catch-finally-statement.md) oluşturulması.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally Deyimi](../../../language-reference/statements/try-catch-finally-statement.md)
- [Visual Basic dizelere giriş](introduction-to-strings.md)
- [Dizeler](index.md)
