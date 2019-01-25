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
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="5174c-102">İfade türüne sahip &#39; &lt;typename&gt; &#39; kısıtlanmış bir tür olan ve öğesinden devralınan üyelere erişim için kullanılamaz &#39;nesne&#39; veya &#39;ValueType&#39;</span><span class="sxs-lookup"><span data-stu-id="5174c-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="5174c-103">Bir ifade, ortak dil çalışma zamanı tarafından (CLR) Kutulu bir türe değerlendirir ancak kutulama gerektiren bir üye erişir.</span><span class="sxs-lookup"><span data-stu-id="5174c-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="5174c-104">*Kutulama* bir türe dönüştürmek için gereken işleme anlamına gelir `Object` veya bazı durumlarda için <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="5174c-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="5174c-105">Ortak dil çalışma zamanı belirli yapı türleri, örneğin kutusunda olamaz <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, ve <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="5174c-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="5174c-106">Bu ifade, devralınan bir yöntemi çağırmak için kısıtlanmış türdeki kullanmayı dener <xref:System.Object> veya <xref:System.ValueType>, gibi <xref:System.Object.GetHashCode%2A> veya <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="5174c-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="5174c-107">Bu yönteme erişmek için Visual Basic bu hataya neden bir örtük Kutulama dönüştürmesi çalıştı.</span><span class="sxs-lookup"><span data-stu-id="5174c-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="5174c-108">**Hata Kimliği:** BC31393</span><span class="sxs-lookup"><span data-stu-id="5174c-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5174c-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5174c-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="5174c-110">İçin alıntı türü değerlendirilen bir ifade bulun.</span><span class="sxs-lookup"><span data-stu-id="5174c-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="5174c-111">Devralınan bir yöntemi çağırmak için çalışır Ekstrenizi bölümü bulun <xref:System.Object> veya <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="5174c-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="5174c-112">Yöntem çağrısının önlemek için deyimi yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="5174c-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5174c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5174c-113">See also</span></span>
- [<span data-ttu-id="5174c-114">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="5174c-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
