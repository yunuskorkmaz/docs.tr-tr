---
title: 'Bu ilk deyimi &#39;Sub New&#39; açık çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; çünkü &#39; &lt;constructorname&gt; &#39; temel sınıfta &#39; &lt;baseclassname&gt; &#39; , &#39; &lt;derivedclassname&gt; &#39; artık kullanılmıyor olarak işaretlendiğinden: &#39; &lt;errormessage&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 9d07a68fd8d9790178427c512375323f23f46772
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566789"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>Bu ilk deyimi &#39;Sub New&#39; açık çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; çünkü &#39; &lt;constructorname&gt; &#39; temel sınıfta &#39; &lt;baseclassname&gt; &#39; , &#39; &lt;derivedclassname&gt; &#39; artık kullanılmıyor olarak işaretlendiğinden: &#39; &lt;errormessage&gt;&#39;
Bir sınıf oluşturucusu bir temel sınıf oluşturucu açıkça çağırmaz ve örtük temel sınıf oluşturucusu ile işaretlenmiş <xref:System.ObsoleteAttribute> özniteliği ve hata olarak değerlendirilecek yönergesi.  
  
 Bir türetilen sınıf oluşturucusu bir temel sınıf oluşturucusunu çağırma değil, Visual Basic bir parametresiz bir temel sınıf oluşturucusu örtük çağrıyla oluşturmaya çalışır. Temel sınıfında bağımsız değişken çağrılabilecek erişilebilir hiçbir oluşturucu ise, Visual Basic örtük çağrıyla oluşturulamıyor. Bu durumda, gerekli Oluşturucusu ile işaretlenmiş <xref:System.ObsoleteAttribute> çağıramaz Visual Basic için özniteliği.  
  
 Herhangi bir programlama öğesi artık uygulayarak kullanımda olarak işaretleyebilirsiniz <xref:System.ObsoleteAttribute> ona. Bunu yaparsanız özniteliğin ayarlayabilirsiniz <xref:System.ObsoleteAttribute.IsError%2A> ya da özellik `True` veya `False`. Ayarlarsanız `True`, derleyici bir hata öğe kullanma girişimi değerlendirir. Ayarlarsanız `False`, veya bu izin varsayılan `False`, öğe kullanma girişimi varsa, derleyici bir uyarı verir.  
  
 **Hata Kimliği:** BC30920  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tırnak işaretli hata iletisini inceleyin ve uygun eylemi gerçekleştirin.  
  
2.  Bir çağrı ekleyin `MyBase.New()` veya `MyClass.New()` ilk deyimi olarak `Sub New` türetilen sınıfta.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)

