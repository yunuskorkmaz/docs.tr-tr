---
title: "New İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a>New İşleci (Visual Basic)
Tanıtır bir `New` yeni bir nesne örneğini oluşturmak için yan tümcesi bir tür parametresi bir oluşturucu kısıtlama belirtir veya tanımlayan bir `Sub` bir sınıf oluşturucu yordamı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bildiriminde ya da atama ifadesi, bir `New` yan tümcesi içinden örneği oluşturulabilir tanımlı bir sınıf belirtmeniz gerekir. Bu sınıf çağıran kodu erişmek için bir veya daha fazla oluşturucular kullanıma gerekir anlamına gelir.  
  
 Kullanabileceğiniz bir `New` bildirimi deyimi veya atama deyiminin yan tümcesi. Deyim çalıştırıldığında, belirtilen sınıfının verdiğiniz herhangi bir bağımsız değişken geçirme uygun oluşturucuyu çağırır. Aşağıdaki örnekte bu örnekleri oluşturarak gösterir. bir `Customer` iki Oluşturucusu vardır sınıfı, parametre almayan diğeri bir dize parametresi alan.  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 Diziler sınıfları olduğundan `New` yeni bir dizi örnek aşağıdaki örneklerde gösterildiği gibi oluşturabilirsiniz.  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 Ortak dil çalışma zamanı (CLR) oluşturur bir <xref:System.OutOfMemoryException> varsa yeni bir örneğini oluşturmak için bellek yetersiz hatası.  
  
> [!NOTE]
>  `New` Anahtar sözcüğü de tür parametresi listelerinde sağlanan türü erişilebilir parametresiz bir kurucusu kullanıma gerekir belirtmek için kullanılır. Tür parametreleri ve kısıtlamaları hakkında daha fazla bilgi için bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).  
  
 Bir sınıf için bir oluşturucu yordam oluşturmak için adını ayarlayın bir `Sub` yordamına `New` anahtar sözcüğü. Daha fazla bilgi için bkz: [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
 `New` Anahtar sözcüğü bu bağlamlarında kullanılabilir:  
  
 [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [,](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.OutOfMemoryException>  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Tür listesi](../../../visual-basic/language-reference/statements/type-list.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Nesne ömrü: Nesneleri oluşturma ve yok etme](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
