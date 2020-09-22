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
ms.openlocfilehash: b982057d2094f807b68d5190dfad388fb9a2c65a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873236"
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
 Gereklidir. Özellikleri, yordamları ve olayları sınıf veya yapıda ilgili Üyeler tarafından uygulanacak olan bir arabirim.  
  
 `interfacemember`  
 Gereklidir. Uygulanan bir arabirimin üyesi.  
  
## <a name="remarks"></a>Açıklamalar  

 Arabirim, arabirimin sarmalarındaki üyeleri (özellikler, yordamlar ve olaylar) temsil eden prototipli türlerin bir koleksiyonudur. Arabirimler yalnızca üyeler için bildirimleri içerir; sınıflar ve yapılar bu üyeleri uygular. Daha fazla bilgi için bkz. [arabirimler](../../programming-guide/language-features/interfaces/index.md).  
  
 `Implements`Deyimin hemen arkasından `Class` veya ifadesini izlemesi gerekir `Structure` .  
  
 Bir arabirim uyguladığınızda, arabiriminde belirtilen tüm üyeleri uygulamanız gerekir. Herhangi bir üyenin atlanması, söz dizimi hatası olarak kabul edilir. Tek bir üyeyi uygulamak için, [Implements](implements-clause.md) `Implements` sınıf veya yapıda üyeyi bildirdiğinizde Implements anahtar sözcüğünü (deyimden ayrı olan) belirtirsiniz. Daha fazla bilgi için bkz. [arabirimler](../../programming-guide/language-features/interfaces/index.md).  
  
 Sınıflar, özelliklerin ve yordamların [özel](../modifiers/private.md) uygulamalarını kullanabilir, ancak bu üyelere yalnızca uygulama sınıfının bir örneğini arabirimin türü olarak belirtilen bir değişkene atama yoluyla erişilebilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Implements` bir arabirimin üyelerini uygulamak için ifadesinin nasıl kullanılacağını gösterir. `ICustomerInfo`Bir olay, özellik ve bir yordam ile adlı bir arabirimi tanımlar. Sınıfı, `customerInfo` arabiriminde tanımlanan tüm üyeleri uygular.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Sınıfının, `customerInfo` `Implements` sınıfın tüm üyelerini uyguladığından emin olmak için deyimin ayrı bir kaynak kod satırında kullandığını unutmayın `ICustomerInfo` . Sonra, sınıftaki her üye, `Implements` Bu arabirim üyesini uyguladığını göstermek için anahtar sözcüğünü kendi üye bildiriminin bir parçası olarak kullanır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki iki yordamda, önceki örnekte uygulanan arabirimi nasıl kullanabileceğiniz gösterilmektedir. Uygulamayı test etmek için projenize bu yordamları ekleyin ve `testImplements` yordamı çağırın.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamalar](implements-clause.md)
- [Interface Deyimi](interface-statement.md)
- [Arabirimler](../../programming-guide/language-features/interfaces/index.md)
