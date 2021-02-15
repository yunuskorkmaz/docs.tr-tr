---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: dize içinde arama (Visual Basic)'
title: 'Nasıl yapılır: dize içinde arama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: dab9faf91eef2e6d845805693227e1a6735ec796
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429746"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Nasıl yapılır: dize içinde arama (Visual Basic)

Bu makalede, Visual Basic bir dize içinde aramanın nasıl yapılacağı hakkında bir örnek gösterilmektedir.

## <a name="example"></a>Örnek

Bu örnek, bir alt <xref:System.String.IndexOf%2A> <xref:System.String> dizenin ilk geçtiği dizini raporlamak için bir nesne üzerindeki yöntemini çağırır:

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>Güçlü programlama

Yöntemi, alt <xref:System.String.IndexOf%2A> dizenin ilk örneğinin ilk karakterinin konumunu döndürür. Dizin 0 tabanlıdır, yani bir dizenin ilk karakterinin 0 dizinine sahip olduğu anlamına gelir.

Alt <xref:System.String.IndexOf%2A> dizeyi bulamazsa,-1 döndürür.

<xref:System.String.IndexOf%2A>Yöntemi, büyük/küçük harfe duyarlıdır ve geçerli kültürü kullanır.

En iyi hata denetimi için, bir try bloğunda dize aramasını kapsamak isteyebilirsiniz.. `Try` [. Yakala... Finally deyiminin](../../../language-reference/statements/try-catch-finally-statement.md) oluşturulması.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.IndexOf%2A>
- [Try...Catch...Finally Deyimi](../../../language-reference/statements/try-catch-finally-statement.md)
- [Visual Basic'de Dizelere Giriş](introduction-to-strings.md)
- [Dizeler](index.md)
