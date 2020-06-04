---
title: İfade kısıtlanmış bir tür olan '<typename>' türüne sahip ve 'Object' veya 'ValueType' öğesinden devralınan üyelere erişim için kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 0eb30488312cc7519f39a6b819aea15489f2f70a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409526"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="12ce8-102">İfade kısıtlanmış bir tür olan '\<typename>' türüne sahip ve 'Object' veya 'ValueType' öğesinden devralınan üyelere erişim için kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="12ce8-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>
<span data-ttu-id="12ce8-103">Bir ifade, ortak dil çalışma zamanı (CLR) tarafından kutulanmamış ancak paketleme gerektiren bir üyeye erişebilen bir tür olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="12ce8-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="12ce8-104">*Kutulama* , bir türü veya ne kadar bir türe dönüştürmek için gereken işleme anlamına gelir `Object` <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="12ce8-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="12ce8-105">Ortak dil çalışma zamanı belirli yapı türlerini (örneğin, ve) <xref:System.ArgIterator> , <xref:System.RuntimeArgumentHandle> <xref:System.TypedReference></span><span class="sxs-lookup"><span data-stu-id="12ce8-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="12ce8-106">Bu ifade, veya gibi devralınan bir yöntemi çağırmak için kısıtlanmış türü kullanmaya çalışır <xref:System.Object> <xref:System.ValueType> <xref:System.Object.GetHashCode%2A> <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="12ce8-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="12ce8-107">Bu yönteme erişmek için Visual Basic, bu hataya neden olan bir örtük paketleme dönüştürmesi denemiştir.</span><span class="sxs-lookup"><span data-stu-id="12ce8-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="12ce8-108">**Hata kimliği:** BC31393</span><span class="sxs-lookup"><span data-stu-id="12ce8-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="12ce8-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="12ce8-109">To correct this error</span></span>  
  
1. <span data-ttu-id="12ce8-110">Alıntı yapılan tür sonucunu veren ifadeyi bulun.</span><span class="sxs-lookup"><span data-stu-id="12ce8-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2. <span data-ttu-id="12ce8-111">Veya ' den devralınan yöntemi çağırmayı deneyen deyiminiz kısmını bulun <xref:System.Object> <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="12ce8-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3. <span data-ttu-id="12ce8-112">Yöntem çağrısından kaçınmak için ifadeyi yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="12ce8-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ce8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12ce8-113">See also</span></span>

- [<span data-ttu-id="12ce8-114">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="12ce8-114">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
