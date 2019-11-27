---
title: Me, My, MyBase ve MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347345"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic'de Me, My, MyBase ve MyClass
Visual Basic 'de `Me`, `My`, `MyBase`ve `MyClass` benzer adlara sahiptir ancak farklı amaçlar vardır. Bu konu, bu varlıkların her birini ayırt edebilmek için açıklar.  
  
## <a name="me"></a>Beni  
 `Me` anahtar sözcüğü, kodun Şu anda yürütüldüğü bir sınıfın veya yapının belirli bir örneğine başvurmak için bir yol sağlar. `Me`, nesne değişkeni ya da geçerli örneğe başvuran bir yapı değişkeni gibi davranır. `Me` kullanmak, bir sınıfın veya yapının Şu anda yürütülmekte olan örneği hakkındaki bilgileri başka bir sınıf, yapı veya modüldeki bir yordama iletmek için özellikle yararlıdır.  
  
 Örneğin, bir modülde aşağıdaki yordama sahip olduğunuzu varsayalım.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Aşağıdaki ifadeyi kullanarak, bu yordamı çağırabilir ve <xref:System.Windows.Forms.Form> sınıfının geçerli örneğini bir bağımsız değişken olarak geçirebilirsiniz.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>My  
 `My` özelliği, Visual Basic kullanıcının bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşime geçmesini sağlayan bir dizi .NET Framework sınıfına kolay ve sezgisel erişim sağlar.  
  
## <a name="mybase"></a>MyBase  
 `MyBase` anahtar sözcüğü, sınıfın geçerli örneğinin temel sınıfına başvuran bir nesne değişkeni gibi davranır. `MyBase`, türetilmiş bir sınıfta geçersiz kılınan veya gölgeli temel sınıf üyelerine erişmek için kullanılır. `MyBase.New`, türetilmiş bir sınıf oluşturucusundan bir taban sınıf oluşturucuyu açıkça çağırmak için kullanılır.  
  
## <a name="myclass"></a>Sınıfım  
 `MyClass` anahtar sözcüğü, başlangıçta uygulanmış olan bir sınıfın geçerli örneğine başvuran bir nesne değişkeni gibi davranır. `MyClass`, `Me`benzerdir, ancak tüm Yöntem çağrıları Yöntem `NotOverridable`olarak değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
