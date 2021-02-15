---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir dizeyi Visual Basic bir karakter dizisine dönüştürme'
title: 'Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: f85b0801cf013e207eacd70a256a3ed0a8dc7887
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476156"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme

Bazen dizinizdeki karakterlerle ilgili verilerin ve dizinizdeki karakterlerin (örneğin, bir dizeyi ayrıştırırken) bulunduğu konumlarda olması yararlı olur. Bu örnek, dizenin metodunu çağırarak bir dizedeki karakterlerin bir dizisini nasıl kullanabileceğinizi gösterir <xref:System.String.ToCharArray%2A> .  
  
## <a name="example"></a>Örnek  

 Bu örnekte bir dizenin bir diziye nasıl bölüneceği `Char` ve bir dizenin `String` Unicode metin karakterlerinin dizisine bölünmesi gösterilmektedir. Bu farkın nedeni, Unicode metin karakterlerinin iki veya daha fazla `Char` karakterden (örneğin, bir vekil çifti veya Birleşik karakter dizisi) oluşmasının nedenidir. Daha fazla bilgi için bkz <xref:System.Globalization.TextElementEnumerator> . ve [Unicode standart](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>Örnek  

 Bir dizeyi Unicode metin karakterlerine bölmek daha zordur, ancak bir dizenin görsel temsili hakkında bilgi gerekirse bu gereklidir. Bu örnek, <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> bir dizeyi oluşturan Unicode metin karakterleri hakkında bilgi almak için yöntemini kullanır.  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Nasıl Yapılır: Dizelerdeki Karakterlere Erişme](how-to-access-characters-in-strings.md)
- [Visual Basic'de Dizeler ve Diğer Veri Türleri Arasında Dönüştürme](converting-between-strings-and-other-data-types.md)
- [Dizeler](index.md)
