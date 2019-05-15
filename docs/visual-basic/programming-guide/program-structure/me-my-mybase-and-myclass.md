---
title: Visual Basic'de Me, My, MyBase ve MyClass
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
ms.openlocfilehash: 3eca756429c5fec8f324a17350844b59baf9ccf7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586259"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a>Visual Basic'de Me, My, MyBase ve MyClass
`Me`, `My`, `MyBase`, ve `MyClass` Visual Basic'te adlarının benzer ancak farklı amaçlara sahip. Bu konuda bunları ayırt etmek için bunların her biri açıklanmaktadır.  
  
## <a name="me"></a>Beni  
 `Me` Anahtar sözcüğü bir sınıf veya yapı içinde kod şu anda Yürütülüyor belirli örneğine başvurmak için bir yol sağlar. `Me` bir nesne değişkeni veya bir yapı değişken geçerli örneğine başvurma gibi davranır. Kullanarak `Me` başka bir sınıf, yapı veya modül bir yordam için bir sınıf veya yapı şu anda yürütülen örneği hakkında bilgi geçirmek için özellikle yararlıdır.  
  
 Örneğin, bir modülde aşağıdaki yordam olduğunu varsayalım.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Bu yordam çağrısı ve geçerli örneğini geçirin <xref:System.Windows.Forms.Form> aşağıdaki deyimi kullanarak bir bağımsız değişken olarak sınıf.  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a>Benim  
 `My` Özellik .NET Framework sınıfları, bilgisayar, uygulama, ayarları, kaynakları ve benzeri ile etkileşim kurmak Visual Basic kullanıcı etkinleştirme sayısını kolay ve sezgisel erişim sağlar.  
  
## <a name="mybase"></a>MyBase  
 `MyBase` Anahtar sözcüğü davranacağını gibi geçerli bir sınıf örneğinin temel sınıfına başvuran bir nesne değişkeni. `MyBase` yaygın olarak geçersiz kılınan ya da türetilen bir sınıfta gölgeli bir temel sınıf üyelerinin erişmek için kullanılır. `MyBase.New` bir temel sınıf oluşturucusu bir türetilmiş sınıf oluşturucusunda açıkça çağırmak için kullanılır.  
  
## <a name="myclass"></a>MyClass  
 `MyClass` Anahtar sözcüğü davranacağını gibi bir nesne değişkeninin özgün olarak uygulandığı bir sınıfın geçerli örneğine başvurma. `MyClass` benzer `Me`, ancak yöntem'ymiş gibi üzerindeki tüm yöntem çağrılarını kabul edilir `NotOverridable`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Devralma Temelleri](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
