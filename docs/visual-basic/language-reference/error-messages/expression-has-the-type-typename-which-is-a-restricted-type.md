---
title: İfade türüne sahip &#39; &lt;typename&gt; &#39; kısıtlanmış bir tür olan ve öğesinden devralınan üyelere erişim için kullanılamaz &#39;nesne&#39; veya &#39;ValueType&#39;
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: d44b9a29f0848508d8cd814e857d9b01819ce7ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535963"
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>İfade türüne sahip &#39; &lt;typename&gt; &#39; kısıtlanmış bir tür olan ve öğesinden devralınan üyelere erişim için kullanılamaz &#39;nesne&#39; veya &#39;ValueType&#39;
Bir ifade, ortak dil çalışma zamanı tarafından (CLR) Kutulu bir türe değerlendirir ancak kutulama gerektiren bir üye erişir.  
  
 *Kutulama* bir türe dönüştürmek için gereken işleme anlamına gelir `Object` veya bazı durumlarda için <xref:System.ValueType>. Ortak dil çalışma zamanı belirli yapı türleri, örneğin kutusunda olamaz <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, ve <xref:System.TypedReference>.  
  
 Bu ifade, devralınan bir yöntemi çağırmak için kısıtlanmış türdeki kullanmayı dener <xref:System.Object> veya <xref:System.ValueType>, gibi <xref:System.Object.GetHashCode%2A> veya <xref:System.Object.ToString%2A>. Bu yönteme erişmek için Visual Basic bu hataya neden bir örtük Kutulama dönüştürmesi çalıştı.  
  
 **Hata Kimliği:** BC31393  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  İçin alıntı türü değerlendirilen bir ifade bulun.  
  
2.  Devralınan bir yöntemi çağırmak için çalışır Ekstrenizi bölümü bulun <xref:System.Object> veya <xref:System.ValueType>.  
  
3.  Yöntem çağrısının önlemek için deyimi yeniden yazın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
