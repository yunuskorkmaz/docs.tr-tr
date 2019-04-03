---
title: "'<constructorname>' öğesinin '<baseclassname>' temel sınıfındaki '<derivedclassname>' kullanılmıyor biçiminde işaretlendiğinden, bu 'Sub New' yönteminin ilk deyimi 'MyBase.New' veya 'MyClass.New' için açık çağrı olmalıdır: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 737f9119814e784ebabcbb4629ab6948ce164168
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814100"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a>Bu 'Sub New' öğesinin ilk deyimi 'MyBase.New' veya 'MyClass.New' için açık çağrı olmalıdır, çünkü '\<constructorname >' temel sınıfındaki\<baseclassname >', '\<derivedclassname >' kullanılmıyor biçiminde işaretlendiğinden: '\< ErrorMessage >'
Bir sınıf oluşturucusu bir temel sınıf oluşturucu açıkça çağırmaz ve örtük temel sınıf oluşturucusu ile işaretlenmiş <xref:System.ObsoleteAttribute> özniteliği ve hata olarak değerlendirilecek yönergesi.  
  
 Bir türetilen sınıf oluşturucusu bir temel sınıf oluşturucusunu çağırma değil, Visual Basic bir parametresiz bir temel sınıf oluşturucusu örtük çağrıyla oluşturmaya çalışır. Temel sınıfında bağımsız değişken çağrılabilecek erişilebilir hiçbir oluşturucu ise, Visual Basic örtük çağrıyla oluşturulamıyor. Bu durumda, gerekli Oluşturucusu ile işaretlenmiş <xref:System.ObsoleteAttribute> çağıramaz Visual Basic için özniteliği.  
  
 Herhangi bir programlama öğesi artık uygulayarak kullanımda olarak işaretleyebilirsiniz <xref:System.ObsoleteAttribute> ona. Bunu yaparsanız özniteliğin ayarlayabilirsiniz <xref:System.ObsoleteAttribute.IsError%2A> ya da özellik `True` veya `False`. Ayarlarsanız `True`, derleyici bir hata öğe kullanma girişimi değerlendirir. Ayarlarsanız `False`, veya bu izin varsayılan `False`, öğe kullanma girişimi varsa, derleyici bir uyarı verir.  
  
 **Hata Kimliği:** BC30920  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tırnak işaretli hata iletisini inceleyin ve uygun eylemi gerçekleştirin.  
  
2.  Bir çağrı ekleyin `MyBase.New()` veya `MyClass.New()` ilk deyimi olarak `Sub New` türetilen sınıfta.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
