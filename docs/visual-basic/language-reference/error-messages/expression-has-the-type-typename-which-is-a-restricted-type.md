---
title: "İfade türü &#39;var; &lt;typename&gt;& kısıtlanmış türdeki ve devralınan üyeler &#39; nesnesi &#39; erişmek için kullanılamaz #39; veya &#39; ValueType &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords: BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30742bd46ccd1a3e5a688ebd2621e2c8a3d50e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="398d3-102">İfade türü &#39;var; &lt;typename&gt;& kısıtlanmış türdeki ve devralınan üyeler &#39; nesnesi &#39; erişmek için kullanılamaz #39; veya &#39; ValueType &#39;</span><span class="sxs-lookup"><span data-stu-id="398d3-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="398d3-103">Bir ifade ortak dil çalışma zamanı tarafından (CLR) Kutulu bir türe değerlendirir ancak kutulama gerektiren üye erişir.</span><span class="sxs-lookup"><span data-stu-id="398d3-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="398d3-104">*Kutulama* türüne dönüştürmek için gereken işleme başvurduğu `Object` veya bazen için <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="398d3-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="398d3-105">Ortak dil çalışma zamanı belirli yapı türleri örneğin kutusunda olamaz <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, ve <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="398d3-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="398d3-106">Bu ifade devralınan bir yöntemi çağırmak için kısıtlanmış türdeki kullanma girişiminde <xref:System.Object> veya <xref:System.ValueType>, gibi <xref:System.Object.GetHashCode%2A> veya <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="398d3-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="398d3-107">Bu yönteme erişmek için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bu hataya neden olan bir örtük kutulama dönüştürme çalıştı.</span><span class="sxs-lookup"><span data-stu-id="398d3-107">To access this method, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="398d3-108">**Hata Kimliği:** BC31393</span><span class="sxs-lookup"><span data-stu-id="398d3-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="398d3-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="398d3-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="398d3-110">Alıntı tür veren ifade bulun.</span><span class="sxs-lookup"><span data-stu-id="398d3-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="398d3-111">Devralınan yöntemini çağırmayı dener deyiminizde bölümünü bulun <xref:System.Object> veya <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="398d3-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="398d3-112">Yöntem çağrısının önlemek için deyimi yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="398d3-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="398d3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="398d3-113">See Also</span></span>  
 [<span data-ttu-id="398d3-114">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="398d3-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
