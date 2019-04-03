---
title: New İşleci (Visual Basic)
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
ms.openlocfilehash: 630b0c48def77449f426b287a26f95af7cfb930e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837739"
---
# <a name="new-operator-visual-basic"></a>New İşleci (Visual Basic)
Tanıtır bir `New` yan tümcesi, yeni bir nesne örneği oluşturmak için bir tür parametresinde Oluşturucu kısıtlaması belirtir ya da tanımlayan bir `Sub` sınıf oluşturucusunu yordamı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bildirimi veya atama ifadesi bir `New` yan tümcesinin içinden örneği oluşturulabilir tanımlanmış bir sınıf belirtmeniz gerekir. Bu sınıf çağıran kod erişebilen bir veya daha fazla Oluşturucu kullanıma açmalıdır anlamına gelir.  
  
 Kullanabileceğiniz bir `New` yan tümcesinde bir bildirim deyiminin veya atama ifadesi. Deyim çalıştırıldığında, belirtilen sınıfın verdiğiniz herhangi bir bağımsız değişken geçirme uygun oluşturucuyu çağırır. Aşağıdaki örnek bu örnekleri oluşturarak gösterir. bir `Customer` sınıfın iki Oluşturucusu vardır, yani parametre almayan diğeri bir dize parametresi alan.  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 Diziler sınıfları olduğundan `New` aşağıdaki örneklerde gösterildiği gibi yeni bir dizi örneği oluşturabilirsiniz.  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 Ortak dil çalışma zamanı (CLR) bir <xref:System.OutOfMemoryException> varsa yeni bir örneğini oluşturmak için yetersiz bellek hatası.  
  
> [!NOTE]
>  `New` Anahtar sözcüğü de türü parametre listelerindeki sağlanan tür erişilebilir parametresiz bir oluşturucu kullanıma açmalıdır belirtmek için kullanılır. Tür parametreleri ve kısıtlamaları hakkında daha fazla bilgi için bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Bir sınıf için bir oluşturucu yordam oluşturmak için kümesinin adı bir `Sub` yordama `New` anahtar sözcüğü. Daha fazla bilgi için [nesne ömrü: Nesneler nasıl oluşturulur ve imha](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 `New` Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [,](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.OutOfMemoryException>
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
