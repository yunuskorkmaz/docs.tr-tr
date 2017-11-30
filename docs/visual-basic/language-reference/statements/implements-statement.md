---
title: Implements Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1103305ffbf5425d9a6a6a09695437968642710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Arabirimleri](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
