---
title: İfade türü sahip &#39; &lt;typename&gt; &#39; kısıtlanmış bir türde olduğundan ve devralınan üyeler erişmek için kullanılamaz &#39;nesne&#39; veya &#39;ValueType&#39;
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 2ba2298da77ac31abc0b1b4ad84328be7bc6dbb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587579"
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>İfade türü sahip &#39; &lt;typename&gt; &#39; kısıtlanmış bir türde olduğundan ve devralınan üyeler erişmek için kullanılamaz &#39;nesne&#39; veya &#39;ValueType&#39;
Bir ifade ortak dil çalışma zamanı tarafından (CLR) Kutulu bir türe değerlendirir ancak kutulama gerektiren üye erişir.  
  
 *Kutulama* türüne dönüştürmek için gereken işleme başvurduğu `Object` veya bazen için <xref:System.ValueType>. Ortak dil çalışma zamanı belirli yapı türleri örneğin kutusunda olamaz <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, ve <xref:System.TypedReference>.  
  
 Bu ifade devralınan bir yöntemi çağırmak için kısıtlanmış türdeki kullanma girişiminde <xref:System.Object> veya <xref:System.ValueType>, gibi <xref:System.Object.GetHashCode%2A> veya <xref:System.Object.ToString%2A>. Bu yönteme erişmek için Visual Basic bu hataya neden olan bir örtük kutulama dönüştürme çalıştı.  
  
 **Hata Kimliği:** BC31393  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Alıntı tür veren ifade bulun.  
  
2.  Devralınan yöntemini çağırmayı dener deyiminizde bölümünü bulun <xref:System.Object> veya <xref:System.ValueType>.  
  
3.  Yöntem çağrısının önlemek için deyimi yeniden yazın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
