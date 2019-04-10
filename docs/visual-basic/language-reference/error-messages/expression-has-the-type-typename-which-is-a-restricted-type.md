---
title: İfade kısıtlanmış bir tür olan '<typename>' türüne sahip ve 'Object' veya 'ValueType' öğesinden devralınan üyelere erişim için kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 017a2458562068727674bd3fd9cda8c33d989e8b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314626"
---
# <a name="expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="0384d-102">İfade türüne sahip '\<typename >' kısıtlanmış bir tür olan ve 'Object' veya 'ValueType' öğesinden devralınan üyelere erişim için kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="0384d-102">Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>
<span data-ttu-id="0384d-103">Bir ifade, ortak dil çalışma zamanı tarafından (CLR) Kutulu bir türe değerlendirir ancak kutulama gerektiren bir üye erişir.</span><span class="sxs-lookup"><span data-stu-id="0384d-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="0384d-104">*Kutulama* bir türe dönüştürmek için gereken işleme anlamına gelir `Object` veya bazı durumlarda için <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="0384d-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="0384d-105">Ortak dil çalışma zamanı belirli yapı türleri, örneğin kutusunda olamaz <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, ve <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="0384d-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="0384d-106">Bu ifade, devralınan bir yöntemi çağırmak için kısıtlanmış türdeki kullanmayı dener <xref:System.Object> veya <xref:System.ValueType>, gibi <xref:System.Object.GetHashCode%2A> veya <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="0384d-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="0384d-107">Bu yönteme erişmek için Visual Basic bu hataya neden bir örtük Kutulama dönüştürmesi çalıştı.</span><span class="sxs-lookup"><span data-stu-id="0384d-107">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="0384d-108">**Hata Kimliği:** BC31393</span><span class="sxs-lookup"><span data-stu-id="0384d-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0384d-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0384d-109">To correct this error</span></span>  
  
1. <span data-ttu-id="0384d-110">İçin alıntı türü değerlendirilen bir ifade bulun.</span><span class="sxs-lookup"><span data-stu-id="0384d-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2. <span data-ttu-id="0384d-111">Devralınan bir yöntemi çağırmak için çalışır Ekstrenizi bölümü bulun <xref:System.Object> veya <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="0384d-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3. <span data-ttu-id="0384d-112">Yöntem çağrısının önlemek için deyimi yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="0384d-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0384d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0384d-113">See also</span></span>

- [<span data-ttu-id="0384d-114">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="0384d-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
