---
title: "Son &lt;anahtar sözcüğü&gt; deyimi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf0ac1221f8a85a8a43599d9c5ec210884205e5e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a><span data-ttu-id="4e980-102">Son &lt;anahtar sözcüğü&gt; deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e980-102">End &lt;keyword&gt; Statement (Visual Basic)</span></span>
<span data-ttu-id="4e980-103">Bir ek anahtar sözcüğüyle izlendiğinde, bu anahtar tarafından sunulan deyimi blok tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4e980-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e980-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e980-104">Syntax</span></span>  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="4e980-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4e980-105">Parts</span></span>  
 `End`  
 <span data-ttu-id="4e980-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4e980-106">Required.</span></span> <span data-ttu-id="4e980-107">Programlama öğesi tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4e980-107">Terminates the definition of the programming element.</span></span>  
  
 `AddHandler`  
 <span data-ttu-id="4e980-108">Sonlandırmak için gerekli bir `AddHandler` eşleşen bir başlamış erişimcisi `AddHandler` özel deyiminde [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-108">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Class`  
 <span data-ttu-id="4e980-109">Eşleşen bir başlamış bir sınıf tanımı sonlandırmak için gerekli [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-109">Required to terminate a class definition begun by a matching [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
 `Enum`  
 <span data-ttu-id="4e980-110">Eşleşen bir başlamış bir numaralandırma tanımı sonlandırmak için gerekli [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-110">Required to terminate an enumeration definition begun by a matching [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 `Event`  
 <span data-ttu-id="4e980-111">Sonlandırmak için gerekli bir `Custom` eşleşen bir başlamış olay tanımı [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-111">Required to terminate a `Custom` event definition begun by a matching [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Function`  
 <span data-ttu-id="4e980-112">Sonlandırmak için gerekli bir `Function` eşleşen bir başlamış yordamı tanımı [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-112">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="4e980-113">Yürütme karşılaşırsa bir `End``Function` deyimi, Denetim çağıran kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e980-113">If execution encounters an `End``Function` statement, control returns to the calling code.</span></span>  
  
 `Get`  
 <span data-ttu-id="4e980-114">Sonlandırmak için gerekli bir `Property` eşleşen bir başlamış yordamı tanımı [alma deyimi](../../../visual-basic/language-reference/statements/get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-114">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md).</span></span> <span data-ttu-id="4e980-115">Yürütme karşılaşırsa bir `End``Get` deyimi, özelliğin değerini isteyen deyimi denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e980-115">If execution encounters an `End``Get` statement, control returns to the statement requesting the property's value.</span></span>  
  
 `If`  
 <span data-ttu-id="4e980-116">Sonlandırmak için gerekli bir `If`... `Then`... `Else` engelleme eşleşen bir başlamış tanımı `If` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4e980-116">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="4e980-117">Bkz: [varsa... Then... Else deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-117">See [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span>  
  
 `Interface`  
 <span data-ttu-id="4e980-118">Eşleşen bir başlamış bir arabirim tanımı sonlandırmak için gerekli [arabirimi deyimi](../../../visual-basic/language-reference/statements/interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-118">Required to terminate an interface definition begun by a matching [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md).</span></span>  
  
 `Module`  
 <span data-ttu-id="4e980-119">Eşleşen bir başlamış bir modül tanımı sonlandırmak için gerekli [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-119">Required to terminate a module definition begun by a matching [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
 `Namespace`  
 <span data-ttu-id="4e980-120">Eşleşen bir başlamış bir ad alanı tanımını sonlandırmak için gerekli [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-120">Required to terminate a namespace definition begun by a matching [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span>  
  
 `Operator`  
 <span data-ttu-id="4e980-121">Eşleşen bir başlamış bir işleç tanımı sonlandırmak için gerekli [Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-121">Required to terminate an operator definition begun by a matching [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 `Property`  
 <span data-ttu-id="4e980-122">Eşleşen bir başlamış özellik tanımı sonlandırmak için gerekli [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-122">Required to terminate a property definition begun by a matching [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
 `RaiseEvent`  
 <span data-ttu-id="4e980-123">Sonlandırmak için gerekli bir `RaiseEvent` eşleşen bir başlamış erişimcisi `RaiseEvent` özel deyiminde [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-123">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `RemoveHandler`  
 <span data-ttu-id="4e980-124">Sonlandırmak için gerekli bir `RemoveHandler` eşleşen bir başlamış erişimcisi `RemoveHandler` özel deyiminde [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-124">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Select`  
 <span data-ttu-id="4e980-125">Sonlandırmak için gerekli bir `Select`... `Case` engelleme eşleşen bir başlamış tanımı `Select` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4e980-125">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="4e980-126">Bkz: [seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-126">See [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
 `Set`  
 <span data-ttu-id="4e980-127">Sonlandırmak için gerekli bir `Property` eşleşen bir başlamış yordamı tanımı [Set deyimi](../../../visual-basic/language-reference/statements/set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-127">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md).</span></span> <span data-ttu-id="4e980-128">Yürütme karşılaşırsa bir `End``Set` deyimi, özelliğin değerini ayarlama deyimi denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e980-128">If execution encounters an `End``Set` statement, control returns to the statement setting the property's value.</span></span>  
  
 `Structure`  
 <span data-ttu-id="4e980-129">Eşleşen bir başlamış bir yapı tanımı sonlandırmak için gerekli [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-129">Required to terminate a structure definition begun by a matching [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
 `Sub`  
 <span data-ttu-id="4e980-130">Sonlandırmak için gerekli bir `Sub` eşleşen bir başlamış yordamı tanımı [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-130">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span> <span data-ttu-id="4e980-131">Yürütme karşılaşırsa bir `End``Sub` deyimi, Denetim çağıran kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e980-131">If execution encounters an `End``Sub` statement, control returns to the calling code.</span></span>  
  
 `SyncLock`  
 <span data-ttu-id="4e980-132">Sonlandırmak için gerekli bir `SyncLock` engelleme eşleşen bir başlamış tanımı `SyncLock` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4e980-132">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="4e980-133">Bkz: [SyncLock deyimi](../../../visual-basic/language-reference/statements/synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-133">See [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md).</span></span>  
  
 `Try`  
 <span data-ttu-id="4e980-134">Sonlandırmak için gerekli bir `Try`... `Catch`... `Finally` engelleme eşleşen bir başlamış tanımı `Try` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4e980-134">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="4e980-135">Bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-135">See [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 `While`  
 <span data-ttu-id="4e980-136">Sonlandırmak için gerekli bir `While` döngü eşleşen bir başlamış tanımı `While` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4e980-136">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="4e980-137">Bkz: [sırada... End While deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-137">See [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
 `With`  
 <span data-ttu-id="4e980-138">Sonlandırmak için gerekli bir `With` engelleme eşleşen bir başlamış tanımı `With` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4e980-138">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="4e980-139">Bkz: [ile... End With deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-139">See [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e980-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e980-140">Remarks</span></span>  
 <span data-ttu-id="4e980-141">[End deyimi](../../../visual-basic/language-reference/statements/end-statement.md), yürütme hemen bir ek anahtar sözcüğü sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4e980-141">The [End Statement](../../../visual-basic/language-reference/statements/end-statement.md), without an additional keyword, terminates execution immediately.</span></span>  
  
 <span data-ttu-id="4e980-142">Sayı işareti önlerine (`#`), `End` anahtar sözcüğü karşılık gelen yönergesi tarafından sunulan önişlem bir blok sona erer.</span><span class="sxs-lookup"><span data-stu-id="4e980-142">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  
  
 `#End`  
 <span data-ttu-id="4e980-143">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="4e980-143">Required.</span></span> <span data-ttu-id="4e980-144">Önişlem blok tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4e980-144">Terminates the definition of the preprocessing block.</span></span>  
  
 `#ExternalSource`  
 <span data-ttu-id="4e980-145">Eşleşen bir başlamış bir dış kaynağa bloğu sonlandırmak için gerekli [#ExternalSource yönergesi](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-145">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span></span>  
  
 `#If`  
 <span data-ttu-id="4e980-146">Eşleşen bir başlamış koşullu derleme bloğunu sonlandırmak için gerekli `#If` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="4e980-146">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="4e980-147">Bkz: [#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-147">See [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span></span>  
  
 `#Region`  
 <span data-ttu-id="4e980-148">Eşleşen bir başladı Kaynak bölgesi bloğunu sonlandırmak için gerekli [#Region yönergesi](../../../visual-basic/language-reference/directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="4e980-148">Required to terminate a source region block begun by a matching [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md).</span></span>  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="4e980-149">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="4e980-149">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="4e980-150">`End` Bir ek anahtar sözcüğü olmadan deyimi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="4e980-150">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e980-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e980-151">See Also</span></span>  
 [<span data-ttu-id="4e980-152">End deyimi</span><span class="sxs-lookup"><span data-stu-id="4e980-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
