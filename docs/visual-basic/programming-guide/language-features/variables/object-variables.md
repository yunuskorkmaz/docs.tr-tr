---
title: Nesne Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7eb860bc732f923316b8ce1d7b94ecdb368bfec3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351789"
---
# <a name="object-variables-in-visual-basic"></a>Visual Basic'de Nesne Değişkenleri

Değerleri doğrudan depolamanın yanı sıra bir değişken bir nesneye başvurabilir. Bir değişkene herhangi bir değer atadığınız nedenlerle bir nesne atayabilirsiniz:

- Değişken adı genellikle daha kısadır ve nesneye erişmek için gereken yöntemlerin ve özelliklerin tam yolundan daha kolay anımsanacak.

- Bir nesneye başvuran bir değişken kullanmak, gerekli yöntemler veya özellikler aracılığıyla nesnenin kendine sürekli olarak erişilmesinin daha etkilidir.

- Kodunuzun çalıştığı sırada diğer nesnelere başvurmak için bir değişken değiştirebilirsiniz.

## <a name="making-code-shorter"></a>Kodu daha kısa hale getirme

Yazmanız istediğiniz kodu kısaltmak için nesne değişkenlerini kullanabilirsiniz. Aşağıdaki örnek, <xref:System.Windows.Forms.Control> nesnesine erişmek için yöntemlerin ve özelliklerin tam yolunu kullanır.

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

Denetim için bir nesne değişkeni kullanıyorsanız, bu kodu kısaltabilir ve yürütmeyi hızlandıraseçebilirsiniz. Nesne değişkenini kendisine atamak istediğiniz belirli bir sınıfla bildirmeniz gerekir (Bu durumda`Control`). Değişkene bir nesne atadıktan sonra, başvurduğu nesneyi değerlendirdiğiniz kadar tam olarak aynı şekilde davranır. Nesnenin özelliklerini ayarlayabilir veya alabilir ya da yöntemlerinden birini kullanabilirsiniz. Aşağıdaki örnek, önceki örnekteki kodu basitleştirmek için bir nesne değişkeni kullanır.

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a>Ayrıca bkz.

- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [Nesne Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Nesne Değişkeni Ataması](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nesne Değişkeni Değerleri](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
