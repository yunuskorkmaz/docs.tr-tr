---
title: 'Nasıl yapılır: Visual Basic StringBuilder kullanarak dize oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 19e036abc9d25ec7fdfd6c33ebb420ec4f503cbc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700102"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Nasıl yapılır: Visual Basic StringBuilder kullanarak dize oluşturma

Bu örnek <xref:System.Text.StringBuilder> sınıfını kullanarak birçok küçük dizeden uzun bir dize oluşturur. @No__t-0 sınıfı, çok sayıda dizeyi birleştirirken `&=` işlecinden daha etkilidir.

## <a name="example"></a>Örnek

Aşağıdaki örnek <xref:System.Text.StringBuilder> sınıfının bir örneğini oluşturur, bu örneğe 1.000 dizelerini ekler ve sonra dize gösterimini döndürür:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Ayrıca bkz.

- [StringBuilder Sınıfını Kullanma](../../../../standard/base-types/stringbuilder.md)
- [&= İşleci](../../../language-reference/operators/and-assignment-operator.md)
- [Dizeler](index.md)
- [Yeni Dizeler Oluşturma](../../../../standard/base-types/creating-new.md)
- [Dizeleri Düzenleme](../../../../standard/base-types/manipulating-strings.md)
