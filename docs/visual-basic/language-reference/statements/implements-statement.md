---
title: Implements Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 5afc7e4e3a03dfab1288e50e65e5076bdd438f7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604217"
---
# <a name="implements-statement"></a>Implements Deyimi
Bir veya daha fazla arabirimleri veya sınıfında uygulanan arabirim üyeleri veya göründüğü yapı tanımı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Bölümler  
 `interfacename`  
 Gerekli. Sınıf veya yapı karşılık gelen üyeleri tarafından uygulanacak, özellikler, yordamlar ve olayları olan bir arabirim.  
  
 `interfacemember`  
 Gerekli. Uygulanan bir arabirim üye.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir koleksiyonu bir arabirimdir prototipler oluşturmayı üyeleri (özellikleri, yordamlar ve olayları) temsil eden arabirim yalıtır. Arabirimleri yalnızca üyeleri için bildirimleri içerir; sınıfları ve yapıları bu üyeleri uygular. Daha fazla bilgi için bkz: [arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 `Implements` Deyimi hemen uymalıdır `Class` veya `Structure` deyimi.  
  
 Arabirim uyguladığınızda arabirimde bildirilen tüm üyeleri uygulamalıdır. Herhangi bir üyenin atlama bir sözdizimi hatası olarak kabul edilir. Ayrı bir üyesiyle uygulamak için belirttiğiniz [uygulayan](../../../visual-basic/language-reference/statements/implements-clause.md) anahtar sözcüğü (ayrı olduğu `Implements` deyimi) bildirme zaman sınıf veya yapı üye. Daha fazla bilgi için bkz: [arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Sınıfları kullanma [özel](../../../visual-basic/language-reference/modifiers/private.md) özellikleri ve yordamları, ancak bu üyeleri uygulamalarıdır yalnızca uygulama sınıfının bir örneğini bir değişkenin içine bildirilen arabirimi türünde olmasını atama tarafından erişilebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `Implements` bir arabirim üyelerini uygulama bildirimi. Adlı bir arabirim tanımlar `ICustomerInfo` bir olay, bir özellik ve bir yordam. Sınıf `customerInfo` arabiriminde tanımlanan tüm üyeleri uygular.  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 Unutmayın sınıfı `customerInfo` kullanan `Implements` sınıfın tüm üyelerini uygulayan göstermek için ayrı bir kaynak kod satırdaki deyim `ICustomerInfo` arabirimi. Her üye sınıfında kullanır `Implements` anahtar sözcüğü bu arabirim üyesini uygulayan belirtmek için üye bildiriminden bir parçası olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki iki yordamdan önceki örnekte uygulanan arabirimi nasıl kullanabileceğinizi gösterir. Uygulanmasını test etmek için bu yordamları, proje çağrısı ekleyin ve `testImplements` yordamı.  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygular](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
