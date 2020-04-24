---
title: 'Nasıl: StringBuilder kullanarak dizeleri oluşturmak'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645333"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Nasıl: Visual Basic bir StringBuilder kullanarak dizeleri oluşturmak

Bu örnek, <xref:System.Text.StringBuilder> sınıfı kullanarak birçok küçük dizeleri uzun bir dize inşa eder. Sınıf, <xref:System.Text.StringBuilder> birçok dizeleri `&=` biraraya getirmek için işleçten daha verimlidir.

## <a name="example"></a>Örnek

Aşağıdaki <xref:System.Text.StringBuilder> örnek, sınıfın bir örneğini oluşturur, bu örneğe 1.000 dize ekler ve dize gösterimini döndürür:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Ayrıca bkz.

- [StringBuilder Sınıfını Kullanma](../../../../standard/base-types/stringbuilder.md)
- [&= Operatör](../../../language-reference/operators/and-assignment-operator.md)
- [Dizeler](index.md)
- [Yeni Dizeler Oluşturma](../../../../standard/base-types/creating-new.md)
- [Dizeleri Düzenleme](../../../../standard/base-types/best-practices-strings.md)
