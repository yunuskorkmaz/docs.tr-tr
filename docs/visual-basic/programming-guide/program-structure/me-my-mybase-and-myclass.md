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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400850"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic'de Me, My, MyBase ve MyClass
`Me`, `My` `MyBase`, `MyClass` , , ve Visual Basic'te benzer adlar vardır, ancak farklı amaçlara sahiptir. Bu konu, bunları ayırt etmek için bu varlıkların her birini açıklar.  
  
## <a name="me"></a>Ben  
 Anahtar `Me` kelime, kodun şu anda yürütüldettiği bir sınıfın veya yapının belirli örneğine başvurmak için bir yol sağlar. `Me`bir nesne değişkeni veya geçerli örne atıfta bulunan bir yapı değişkeni gibi olur. Kullanmak, `Me` özellikle bir sınıfın veya yapının şu anda yürütülen örneği hakkında başka bir sınıf, yapı veya modüldeki bir yordamhakkında bilgi aktarmak için yararlıdır.  
  
 Örneğin, bir modülde aşağıdaki yordamı gördüğünüzün olduğunu varsayalım.  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Aşağıdaki deyimi kullanarak bu yordamı arayabilir <xref:System.Windows.Forms.Form> ve sınıfın geçerli örneğini bağımsız değişken olarak geçirebilirsiniz.  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Benim  
 Bu `My` özellik, Visual Basic kullanıcısının bilgisayar, uygulama, ayarlar, kaynaklar ve benzeri şeylerle etkileşimkurmasını sağlayarak bir dizi .NET Framework sınıfına kolay ve sezgisel erişim sağlar.  
  
## <a name="mybase"></a>Mybase  
 Anahtar `MyBase` kelime, bir sınıfın geçerli örneğinin taban sınıfına atıfta bulunan bir nesne değişkeni gibi olur. `MyBase`türemiş bir sınıfta geçersiz kılınan veya gölgelenen taban sınıf üyelerine erişmek için genellikle kullanılır. `MyBase.New`türemiş bir sınıf oluşturucudan taban sınıf oluşturucusu çağırmak için kullanılır.  
  
## <a name="myclass"></a>Myclass  
 Anahtar `MyClass` kelime, başlangıçta uygulanan bir sınıfın geçerli örneğine atıfta bulunan bir nesne değişkeni gibi olur. `MyClass``Me`benzer, ancak tüm yöntem çağrıları yöntem gibi `NotOverridable`kabul edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
