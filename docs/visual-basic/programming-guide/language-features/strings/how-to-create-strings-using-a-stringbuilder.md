---
title: 'Nasıl yapılır: StringBuilder kullanarak dize oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 9295b9d0cdcfdb05dfc75f75f48c16c2354b09b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344375"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Nasıl yapılır: Visual Basic StringBuilder kullanarak dize oluşturma

Bu örnek, <xref:System.Text.StringBuilder> sınıfını kullanarak çok sayıda daha küçük dizeden uzun bir dize oluşturur. <xref:System.Text.StringBuilder> sınıfı, çok sayıda dizeyi birleştirirken `&=` işleçinden daha etkilidir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Text.StringBuilder> sınıfının bir örneğini oluşturur, bu örneğe 1.000 dizelerini ekler ve sonra dize gösterimini döndürür:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Ayrıca bkz.

- [StringBuilder Sınıfını Kullanma](../../../../standard/base-types/stringbuilder.md)
- [&= İşleci](../../../language-reference/operators/and-assignment-operator.md)
- [Dizeler](index.md)
- [Yeni Dizeler Oluşturma](../../../../standard/base-types/creating-new.md)
- [Dizeleri Düzenleme](../../../../standard/base-types/manipulating-strings.md)
