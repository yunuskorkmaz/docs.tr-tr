---
title: Visual Basic'de Nesne Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 8383261c1806732c4c8abea9834000f003a848a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="object-variables-in-visual-basic"></a>Visual Basic'de Nesne Değişkenleri
Bir değişken değerlerini doğrudan depolama yanı sıra, bir nesneye başvurabilir. Aynı nedenden dolayı bir değişkene herhangi bir değer atamak için bir nesne bir değişkene atayın:  
  
-   Bir değişken adı daha kısa ve yöntemleri ve özellikleri nesnesine erişmek gerekli tam yolunu anımsaması kolay görülür.  
  
-   Nesneye başvuran bir değişkeni kullanarak, art arda nesne özellikleri ve gerekli yöntemleri erişimden çok daha etkilidir.  
  
-   Kodunuzun çalıştığı sırada başka nesnelere atıfta için bir değişken değiştirebilirsiniz.  
  
## <a name="making-code-shorter"></a>Kod kısa yapma  
 Nesne değişkenleri yazmak zorunda kod kısaltmak için kullanabilirsiniz. Aşağıdaki örnek, erişmek için yöntemler ve özellikler tam yolunu kullanır. bir <xref:System.Windows.Forms.Control> nesnesi.  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 Bu kod kısaltın ve denetim için bir nesne değişkeni kullanırsanız yürütmesini kurma hızı. Nesne değişkeni atamak istediğiniz belirli sınıfı ile bildirmelisiniz (`Control` bu durumda). Değişkenine bir nesne atadıktan sonra başvurduğu nesne işlemek gibi onu tam olarak aynı şekilde davranabilirsiniz. Ayarlayabilir veya nesne özelliklerini al veya yöntemlerinden birini kullanın. Aşağıdaki örnek, önceki örnekte kodu basitleştirmek için bir nesne değişkeni kullanır.  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
