---
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
ms.openlocfilehash: 27b5b4516ef729045036c36fedc24b6c576a4f61
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348313"
---
# <a name="new-operator-visual-basic"></a>New İşleci (Visual Basic)

Yeni bir nesne örneği oluşturmak için bir `New` yan tümcesi tanıtır, bir tür parametresinde Oluşturucu kısıtlamasını belirtir veya bir `Sub` yordamını sınıf oluşturucusu olarak tanımlar.

## <a name="remarks"></a>Açıklamalar

Bir bildirimde veya atama ifadesinde, bir `New` yan tümcesi, örneği oluşturulabilecek tanımlanmış bir sınıf belirtmelidir. Bu, sınıfın, çağıran kodun erişebileceği bir veya daha fazla Oluşturucu kullanıma sunması gerektiği anlamına gelir.

Bir bildirim ifadesinde veya atama ifadesinde bir `New` yan tümcesi kullanabilirsiniz. İfade çalıştırıldığında, belirtilen sınıfın uygun oluşturucusunu çağırarak, sağladığınız tüm bağımsız değişkenleri geçer. Aşağıdaki örnek, iki Oluşturucusu olan bir `Customer` sınıfın örnekleri oluşturarak bunu gösterir ve bir parametre ve bir dize parametresi alan bir parametre alır:

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

Diziler sınıflar olduğundan, aşağıdaki örnekte gösterildiği gibi, `New` yeni bir dizi örneği oluşturabilir:

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

Yeni örneği oluşturmak için yeterli bellek yoksa ortak dil çalışma zamanı (CLR) <xref:System.OutOfMemoryException> hatası oluşturur.

> [!NOTE]
> `New` anahtar sözcüğü, sağlanan türün erişilebilir parametresiz bir oluşturucuyu kullanıma sunması gerektiğini belirtmek için tür parametresi listelerinde de kullanılır. Tür parametreleri ve kısıtlamaları hakkında daha fazla bilgi için bkz. [tür listesi](../statements/type-list.md).

Bir sınıf için bir Oluşturucu yordamı oluşturmak için, bir `Sub` yordamının adını `New` anahtar sözcüğüne ayarlayın. Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

`New` anahtar sözcüğü şu bağlamlarda kullanılabilir:

- [Dim Deyimi](../statements/dim-statement.md)
- [Durumunu](../statements/of-clause.md)
- [Sub Deyimi](../statements/sub-statement.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.OutOfMemoryException>
- [Anahtar Sözcükler](../keywords/index.md)
- [Tür Listesi](../statements/type-list.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
