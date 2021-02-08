---
description: "Hakkında daha fazla bilgi edinin: BC31393: Ifadesi <typename> kısıtlanmış bir tür olan ' ' türüne sahip ve ' Object ' veya ' ValueType ' öğesinden devralınan üyelere erişim için kullanılamaz"
title: İfade kısıtlanmış bir tür olan '<typename>' türüne sahip ve 'Object' veya 'ValueType' öğesinden devralınan üyelere erişim için kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 3b5f9bbb85d1645936286ea0e907e3e25764f69a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796385"
---
# <a name="bc31393-expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a><span data-ttu-id="2cb31-103">BC31393: Ifadesi \<typename> kısıtlanmış bir tür olan ' ' türüne sahip ve ' Object ' veya ' ValueType ' öğesinden devralınan üyelere erişim için kullanılamaz</span><span class="sxs-lookup"><span data-stu-id="2cb31-103">BC31393: Expression has the type '\<typename>' which is a restricted type and cannot be used to access members inherited from 'Object' or 'ValueType'</span></span>

<span data-ttu-id="2cb31-104">Bir ifade, ortak dil çalışma zamanı (CLR) tarafından kutulanmamış ancak paketleme gerektiren bir üyeye erişebilen bir tür olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2cb31-104">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>

 <span data-ttu-id="2cb31-105">*Kutulama* , bir türü veya ne kadar bir türe dönüştürmek için gereken işleme anlamına gelir `Object` <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="2cb31-105">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="2cb31-106">Ortak dil çalışma zamanı belirli yapı türlerini (örneğin, ve) <xref:System.ArgIterator> , <xref:System.RuntimeArgumentHandle> <xref:System.TypedReference></span><span class="sxs-lookup"><span data-stu-id="2cb31-106">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>

 <span data-ttu-id="2cb31-107">Bu ifade, veya gibi devralınan bir yöntemi çağırmak için kısıtlanmış türü kullanmaya çalışır <xref:System.Object> <xref:System.ValueType> <xref:System.Object.GetHashCode%2A> <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="2cb31-107">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="2cb31-108">Bu yönteme erişmek için Visual Basic, bu hataya neden olan bir örtük paketleme dönüştürmesi denemiştir.</span><span class="sxs-lookup"><span data-stu-id="2cb31-108">To access this method, Visual Basic has attempted an implicit boxing conversion that causes this error.</span></span>

 <span data-ttu-id="2cb31-109">**Hata kimliği:** BC31393</span><span class="sxs-lookup"><span data-stu-id="2cb31-109">**Error ID:** BC31393</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2cb31-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2cb31-110">To correct this error</span></span>

1. <span data-ttu-id="2cb31-111">Alıntı yapılan tür sonucunu veren ifadeyi bulun.</span><span class="sxs-lookup"><span data-stu-id="2cb31-111">Locate the expression that evaluates to the cited type.</span></span>

2. <span data-ttu-id="2cb31-112">Veya ' den devralınan yöntemi çağırmayı deneyen deyiminiz kısmını bulun <xref:System.Object> <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="2cb31-112">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>

3. <span data-ttu-id="2cb31-113">Yöntem çağrısından kaçınmak için ifadeyi yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="2cb31-113">Rewrite the statement to avoid the method call.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cb31-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cb31-114">See also</span></span>

- [<span data-ttu-id="2cb31-115">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="2cb31-115">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
