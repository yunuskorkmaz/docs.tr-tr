---
title: Ad &#39; &lt;adı&gt; &#39; bildirilmemiş olan
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26245952a2dc5341dedba6c497c47773b882b49b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="name-39ltnamegt39-is-not-declared"></a>Ad &#39; &lt;adı&gt; &#39; bildirilmemiş olan
Bir deyim programlama bir öğesiyle ancak derleyici tam ada sahip bir öğe bulunamıyor.  
  
 **Hata Kimliği:** BC30451  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvuran deyiminde adının yazımını denetleyin. Visual Basic büyük/küçük harfe duyarlıdır, ancak başka bir değişim yazım tamamen farklı bir ad kabul edilir. Unutmayın alt çizgi (`_`) adının bir parçası ve bu nedenle yazımı parçası.  
  
2.  Üye erişimi işleci olup olmadığını denetleyin (`.`) bir nesne ve onun üyesi arasında. Örneğin, bir <xref:System.Windows.Forms.TextBox> adlı Denetim `TextBox1`erişmek için kendi <xref:System.Windows.Forms.TextBoxBase.Text%2A> yazın özelliği `TextBox1.Text`. Bunun yerine yazarsanız, `TextBox1Text`, farklı bir ad oluşturdunuz.  
  
3.  Yazım denetimi doğru olduğundan ve hiçbir nesne üye erişimi sözdizimini doğru ise, öğenin bildirilmiş doğrulayın. Daha fazla bilgi için bkz: [bildirilen öğeler](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).  
  
4.  Programlama öğesi bildirilmiş, kapsam içinde olup olmadığını denetleyin. Başvuran deyimi programlama öğesi bildirme bölgesinin dışındaki ise, öğe adı nitelemek gerekebilir. Daha fazla bilgi için bkz: [Visual Basic'de kapsam](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirimler ve Sabitlere İlişkin Özet](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Bildirilen Öğe Adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
