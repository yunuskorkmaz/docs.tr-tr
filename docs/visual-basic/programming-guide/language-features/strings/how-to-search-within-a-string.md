---
title: 'Nasıl yapılır: dize içinde arama-Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700068"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Nasıl yapılır: dize içinde arama (Visual Basic)

Bu makalede, Visual Basic bir dize içinde aramanın nasıl yapılacağı hakkında bir örnek gösterilmektedir.

## <a name="example"></a>Örnek

Bu örnek, bir alt dizenin ilk geçtiği dizini raporlamak için bir <xref:System.String> nesnesi üzerinde <xref:System.String.IndexOf%2A> yöntemini çağırır:

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>Güçlü programlama

@No__t-0 yöntemi, alt dizenin ilk oluşumunun ilk karakterinin konumunu döndürür. Dizin 0 tabanlıdır, yani bir dizenin ilk karakterinin 0 dizinine sahip olduğu anlamına gelir.

@No__t-0 alt dizeyi bulamazsa,-1 döndürür.

@No__t-0 yöntemi, büyük/küçük harfe duyarlıdır ve geçerli kültürü kullanır.

En iyi hata denetimi için, bir TRY `Try` bloğunda dize aramasını kapsamak isteyebilirsiniz [... Yakala... Finally deyiminin](../../../language-reference/statements/try-catch-finally-statement.md) oluşturulması.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally Deyimi](../../../language-reference/statements/try-catch-finally-statement.md)
- [Visual Basic dizelere giriş](introduction-to-strings.md)
- [Dizeler](index.md)
