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
ms.openlocfilehash: cc96f39d9dc37b7f1a5d8205e145869fb1b5ecef
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072242"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic'de Me, My, MyBase ve MyClass

`Me`,,, `My` `MyBase` ve `MyClass` Visual Basic de benzer adlara sahiptir ancak farklı amaçlar vardır. Bu konu, bu varlıkların her birini ayırt edebilmek için açıklar.  
  
## <a name="me"></a>Ben  

 `Me`Anahtar sözcüğü, kodun Şu anda yürütüldüğü bir sınıfın veya yapının belirli bir örneğine başvurmak için bir yol sağlar. `Me` bir nesne değişkeni ya da geçerli örneğe başvuran bir yapı değişkeni gibi davranır. Kullanmak `Me` özellikle bir sınıfın veya yapının Şu anda yürütülmekte olan örneği hakkındaki bilgileri başka bir sınıf, yapı veya modüldeki bir yordama iletmek için yararlıdır.  
  
 Örneğin, bir modülde aşağıdaki yordama sahip olduğunuzu varsayalım.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Aşağıdaki ifadeyi kullanarak bu yordamı çağırabilir ve sınıfın geçerli örneğini <xref:System.Windows.Forms.Form> bir bağımsız değişken olarak geçirebilirsiniz.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Benim  

 `My`Özelliği, bir dizi .NET Framework sınıfa kolay ve sezgisel erişim sağlar ve Visual Basic kullanıcının bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşime geçmesini sağlar.  
  
## <a name="mybase"></a>MyBase  

 `MyBase`Anahtar sözcüğü, bir sınıfın geçerli örneğinin temel sınıfına başvuran bir nesne değişkeni gibi davranır. `MyBase` , türetilmiş bir sınıfta geçersiz kılınan veya gölgeli olan temel sınıf üyelerine erişmek için yaygın olarak kullanılır. `MyBase.New` Türetilmiş bir sınıf oluşturucusundan bir temel sınıf oluşturucusunu açıkça çağırmak için kullanılır.  
  
## <a name="myclass"></a>Sınıfım  

 `MyClass`Anahtar sözcüğü, başlangıçta uygulanmış olan bir sınıfın geçerli örneğine başvuran bir nesne değişkeni gibi davranır. `MyClass` , öğesine benzerdir `Me` , ancak tüm Yöntem çağrıları, yöntemi gibi kabul edilir `NotOverridable` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Devralma Temelleri](../language-features/objects-and-classes/inheritance-basics.md)
