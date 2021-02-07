---
description: 'Daha fazla bilgi edinin: New Işleci (Visual Basic)'
title: Yeni İşleç
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: f52dd7606127c7587173de8a78e618ceb3e4681d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665386"
---
# <a name="new-operator-visual-basic"></a>New İşleci (Visual Basic)

Yeni bir `New` nesne örneği oluşturmak için bir yan tümce tanıtır, bir tür parametresinde Oluşturucu kısıtlamasını belirtir veya bir `Sub` yordamı sınıf oluşturucusu olarak tanımlar.

## <a name="remarks"></a>Açıklamalar

Bir bildirimde veya atama ifadesinde, `New` yan tümce, örneği oluşturulabilecek tanımlanmış bir sınıf belirtmelidir. Bu, sınıfın, çağıran kodun erişebileceği bir veya daha fazla Oluşturucu kullanıma sunması gerektiği anlamına gelir.

Bir `New` bildirim ifadesinde veya atama ifadesinde bir yan tümce kullanabilirsiniz. İfade çalıştırıldığında, belirtilen sınıfın uygun oluşturucusunu çağırarak, sağladığınız tüm bağımsız değişkenleri geçer. Aşağıdaki örnek `Customer` , bir parametresi ve bir dize parametresi alan bir parametre alan, iki Oluşturucusu olan bir sınıfın örneklerini oluşturarak bunu gösterir:

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

Diziler sınıflar olduğundan, `New` Aşağıdaki örnekte gösterildiği gibi yeni bir dizi örneği oluşturabilir:

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

Ortak dil çalışma zamanı (CLR), <xref:System.OutOfMemoryException> Yeni örneği oluşturmak için yeterli bellek yoksa bir hata oluşturur.

> [!NOTE]
> `New`Anahtar sözcüğü, sağlanan türün erişilebilir parametresiz bir oluşturucuyu kullanıma sunması gerektiğini belirtmek için tür parametresi listelerinde de kullanılır. Tür parametreleri ve kısıtlamaları hakkında daha fazla bilgi için bkz. [tür listesi](../statements/type-list.md).

Bir sınıf için bir Oluşturucu yordamı oluşturmak için, bir `Sub` yordamın adını `New` anahtar sözcüğe ayarlayın. Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

`New`Anahtar sözcüğü şu bağlamlarda kullanılabilir:

- [Dim Deyimi](../statements/dim-statement.md)
- [Durumunu](../statements/of-clause.md)
- [Sub Deyimi](../statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.OutOfMemoryException>
- [Anahtar sözcükler](../keywords/index.md)
- [Tür Listesi](../statements/type-list.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
