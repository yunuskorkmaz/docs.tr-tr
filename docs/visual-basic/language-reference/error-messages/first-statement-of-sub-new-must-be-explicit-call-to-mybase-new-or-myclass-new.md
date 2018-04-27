---
title: 'Bu ilk deyimi &#39;Sub New&#39; için açık bir çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; çünkü &#39; &lt;constructorname&gt; &#39; temel sınıf &#39; &lt;baseclassname&gt; &#39; , &#39; &lt;derivedclassname&gt; &#39; kullanımdan kaldırılmış olarak işaretlenmiş: &#39; &lt;errormessage&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7690c9dcdb97e63959d2f0e31791d55ee7b09ffc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>Bu ilk deyimi &#39;Sub New&#39; için açık bir çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; çünkü &#39; &lt;constructorname&gt; &#39; temel sınıf &#39; &lt;baseclassname&gt; &#39; , &#39; &lt;derivedclassname&gt; &#39; kullanımdan kaldırılmış olarak işaretlenmiş: &#39; &lt;errormessage&gt;&#39;
Bir sınıf oluşturucu açıkça bir temel sınıf oluşturucu çağırmaz ve örtük temel sınıf oluşturucu ile işaretlenmiş <xref:System.ObsoleteAttribute> özniteliği ve yönergesi hata olarak ele alın.  
  
 Bir türetilmiş sınıf oluşturucu bir temel sınıf oluşturucu çağırmaz başlatıldığında, bir taban sınıf parametresiz oluşturucuya örtük bir çağrı oluşturmak Visual Basic dener. Bağımsız değişkenler çağrılabilir temel sınıf erişilebilir bir oluşturucu yok ise, Visual Basic örtük bir çağrı oluşturulamıyor. Bu durumda, gerekli Oluşturucusu ile işaretlenmiş <xref:System.ObsoleteAttribute> Visual Basic çağıramaz şekilde özniteliği.  
  
 Herhangi bir programlama öğesi artık uygulama tarafından kullanılmakta olarak işaretleyebilirsiniz <xref:System.ObsoleteAttribute> ona. Bunu yaparsanız özniteliğin ayarlayabilirsiniz <xref:System.ObsoleteAttribute.IsError%2A> ya da özellik `True` veya `False`. Ayarlarsanız `True`, hata olarak öğe kullanma girişimi derleyici değerlendirir. Ayarlarsanız `False`, veya bu izin için varsayılan `False`, öğe kullanma girişimi ise derleyici bir uyarı verir.  
  
 **Hata Kimliği:** BC30920  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tırnak işaretli hata iletisini inceleyin ve uygun eylemi gerçekleştirin.  
  
2.  Bir çağrı ekleyin `MyBase.New()` veya `MyClass.New()` ilk ifadesi olarak `Sub New` türetilen sınıfta.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
