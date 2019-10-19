---
title: Implements açıklaması (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 865e99aa0e27591d10fde1465047a2e6bf183bbf
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581787"
---
# <a name="implements-statement"></a>Implements Deyimi
Görüntülenen sınıf veya yapı tanımında uygulanması gereken bir veya daha fazla arabirimi veya arabirim üyesini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Bölümler  
 `interfacename`  
 Gerekli. Özellikleri, yordamları ve olayları sınıf veya yapıda ilgili Üyeler tarafından uygulanacak olan bir arabirim.  
  
 `interfacemember`  
 Gerekli. Uygulanan bir arabirimin üyesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Arabirim, arabirimin sarmalarındaki üyeleri (özellikler, yordamlar ve olaylar) temsil eden prototipli türlerin bir koleksiyonudur. Arabirimler yalnızca üyeler için bildirimleri içerir; sınıflar ve yapılar bu üyeleri uygular. Daha fazla bilgi için bkz. [arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 @No__t_0 deyimin `Class` veya `Structure` deyimden hemen önce izlemesi gerekir.  
  
 Bir arabirim uyguladığınızda, arabiriminde belirtilen tüm üyeleri uygulamanız gerekir. Herhangi bir üyenin atlanması, söz dizimi hatası olarak kabul edilir. Tek bir üyeyi uygulamak için, sınıf veya yapıda üyeyi bildirdiğinizde [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) anahtar sözcüğünü (`Implements` deyimden ayrı) belirtirsiniz. Daha fazla bilgi için bkz. [arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Sınıflar, özelliklerin ve yordamların [özel](../../../visual-basic/language-reference/modifiers/private.md) uygulamalarını kullanabilir, ancak bu üyelere yalnızca uygulama sınıfının bir örneğini arabirimin türü olarak belirtilen bir değişkene atama yoluyla erişilebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir arabirimin üyelerini uygulamak için `Implements` deyimin nasıl kullanılacağını gösterir. Bir olay, özellik ve yordamla birlikte `ICustomerInfo` adlı bir arabirimi tanımlar. Sınıf `customerInfo`, arabirimde tanımlanan tüm üyeleri uygular.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Sınıfının `customerInfo`, sınıfın `ICustomerInfo` arabiriminin tüm üyelerini uyguladığını göstermek için `Implements` ifadesini ayrı bir kaynak kodu satırında kullandığını unutmayın. Sonra, sınıftaki her üye, bu arabirim üyesini uyguladığını göstermek için üye bildiriminin bir parçası olarak `Implements` anahtar sözcüğünü kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki iki yordamda, önceki örnekte uygulanan arabirimi nasıl kullanabileceğiniz gösterilmektedir. Uygulamayı test etmek için bu yordamları projenize ekleyin ve `testImplements` yordamını çağırın.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygular](../../../visual-basic/language-reference/statements/implements-clause.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
