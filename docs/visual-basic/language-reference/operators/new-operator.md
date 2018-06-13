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
ms.openlocfilehash: 0fe511b2c16681d7bab7eeda7c121fcbbaa2f5dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603645"
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
  
 [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [,](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.OutOfMemoryException>  
 [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Tür Listesi](../../../visual-basic/language-reference/statements/type-list.md)  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
