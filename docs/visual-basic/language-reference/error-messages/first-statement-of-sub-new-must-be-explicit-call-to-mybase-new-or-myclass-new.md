---
title: "'<constructorname>' öğesinin '<baseclassname>' temel sınıfındaki '<derivedclassname>' kullanılmıyor biçiminde işaretlendiğinden, bu 'Sub New' yönteminin ilk deyimi 'MyBase.New' veya 'MyClass.New' için açık çağrı olmalıdır: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 33dd15e3f5f5538963597f2b00f4214895e1f47a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403011"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a>'\<constructorname>' öğesinin '\<baseclassname>' temel sınıfındaki '\<derivedclassname>' kullanılmıyor biçiminde işaretlendiğinden, bu 'Sub New' yönteminin ilk deyimi 'MyBase.New' veya 'MyClass.New' için açık çağrı olmalıdır: '\<errormessage>'
Bir sınıf Oluşturucusu bir temel sınıf oluşturucusunu açıkça çağırmaz ve örtük temel sınıf oluşturucusu <xref:System.ObsoleteAttribute> özniteliği ve bir hata olarak değerlendirmek için olan yönergeyle işaretlenir.  
  
 Türetilmiş bir sınıf Oluşturucusu bir temel sınıf oluşturucusu çağırlamadığında, Visual Basic parametresiz temel sınıf oluşturucusuna örtük bir çağrı oluşturmaya çalışır. Temel sınıfta bağımsız değişken olmadan çağrılabilecek erişilebilir bir Oluşturucu yoksa Visual Basic örtük bir çağrı üretemiyor. Bu durumda, gerekli Oluşturucu <xref:System.ObsoleteAttribute> özniteliğiyle işaretlenir, bu nedenle Visual Basic çağrılamıyor.  
  
 Herhangi bir programlama öğesini, bu uygulamaya uygulama tarafından artık kullanımda olmayacak şekilde işaretleyebilirsiniz <xref:System.ObsoleteAttribute> . Bunu yaparsanız özniteliğin <xref:System.ObsoleteAttribute.IsError%2A> özelliğini ya da olarak ayarlayabilirsiniz `True` `False` . Öğesini olarak ayarlarsanız `True` , derleyici bir hata olarak öğeyi kullanma denemesine davranır. Bunu olarak ayarlarsanız `False` veya varsayılan olarak izin verirseniz `False` , öğesini kullanma girişimi varsa derleyici bir uyarı verir.  
  
 **Hata kimliği:** BC30920  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Alıntı yapılan hata iletisini inceleyin ve uygun eylemi gerçekleştirin.  
  
2. `MyBase.New()` `MyClass.New()` Türetilmiş sınıftaki öğesinin ilk ifadesine bir çağrı ekleyin `Sub New` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md)
