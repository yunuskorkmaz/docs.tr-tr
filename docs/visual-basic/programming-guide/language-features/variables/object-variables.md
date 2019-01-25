---
title: Visual Basic'de Nesne Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 046119664fc0277a6a5305d0cf086b4438b13f9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685470"
---
# <a name="object-variables-in-visual-basic"></a>Visual Basic'de Nesne Değişkenleri
Bir değişken değerlerini doğrudan depolama ek olarak, bir nesneye başvurabilir. Aynı nedenden dolayı bir değişkene bir değer atamak için bir nesne değişkenine atayın:  
  
-   Bir değişken adı genellikle daha kısa ve kolay yöntemlere ve özelliklere nesneye erişmek için gereken tam yolunu unutmayın.  
  
-   Bir nesneye başvuruda bulunan bir değişken kullanarak sürekli nesne özellikleri ve gerekli yöntemleri erişimden çok daha verimli olur.  
  
-   Bir değişken, kodunuzun çalıştığı sırada başka nesnelere atıfta değiştirebilirsiniz.  
  
## <a name="making-code-shorter"></a>Kodu kısa yapma  
 Kod yazmak zorunda kısaltmak için nesne değişkenleri kullanabilirsiniz. Aşağıdaki örnek, erişmek için yöntemleri ve özellikleri tam yolunu kullanır. bir <xref:System.Windows.Forms.Control> nesne.  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 Bu kod kısaltın ve denetim için bir nesne değişkeninin kullanırsanız yürütme, hızlandırın. Atamak istediğiniz belirli sınıfı ile nesne değişkeni bildirmelidir (`Control` bu durumda). Bir nesne değişkenine atadığınızda, başvurduğu nesneyi kabul gibi bu tamamen aynı şekilde davranabilirsiniz. Ayarlayabilir veya nesnenin özelliklerini almak veya yöntemlerinden birini kullanın. Aşağıdaki örnek, önceki örnekte kodu basitleştirmek için bir nesne değişkenini kullanır.  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nasıl yapılır: Uzun bir nitelenmiş yola sahip nesneye erişimi hızlandırma](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
