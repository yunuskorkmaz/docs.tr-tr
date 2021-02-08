---
description: 'Daha fazla bilgi edinin: End <keyword> deyiminiz (Visual Basic)'
title: End <keyword> Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: ba21d4ba68a054d77d4f29307d49ed8e82bb6b50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769201"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="d2ced-103">End \<keyword> Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2ced-103">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="d2ced-104">Ardından ek bir anahtar sözcük tarafından izlenen, bu anahtar sözcük tarafından tanıtılan bildiri bloğunun tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d2ced-104">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2ced-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2ced-105">Syntax</span></span>

```vb
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
  
## <a name="parts"></a><span data-ttu-id="d2ced-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d2ced-106">Parts</span></span>

|<span data-ttu-id="d2ced-107">Bölüm</span><span class="sxs-lookup"><span data-stu-id="d2ced-107">Part</span></span>|<span data-ttu-id="d2ced-108">Description</span><span class="sxs-lookup"><span data-stu-id="d2ced-108">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="d2ced-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-109">Required.</span></span> <span data-ttu-id="d2ced-110">Programlama öğesinin tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d2ced-110">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="d2ced-111">`AddHandler` `AddHandler` Özel bir [olay deyimindeki](event-statement.md)eşleşen bir ifade tarafından başlatılan bir erişimciyi sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-111">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="d2ced-112">Eşleşen [sınıf ifadesiyle](class-statement.md)başlatılan bir sınıf tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-112">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="d2ced-113">Bir sabit listesi tanımını sonlandırmak için, eşleşen bir [enum ifadesiyle](enum-statement.md)başlamış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-113">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="d2ced-114">`Custom`Eşleşen bir [olay bildirimiyle](event-statement.md)başlatılan bir olay tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-114">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="d2ced-115">`Function`Eşleşen bir [işlev ifadesiyle](function-statement.md)başlatılan bir yordam tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-115">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="d2ced-116">Yürütme bir `End Function` deyimle karşılaşırsa, Denetim çağıran koda geri döner.</span><span class="sxs-lookup"><span data-stu-id="d2ced-116">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="d2ced-117">`Property`Eşleşen [Get ifadesiyle](get-statement.md)başlatılan bir yordam tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-117">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="d2ced-118">Yürütme bir `End Get` deyimle karşılaşırsa denetim, özelliğin değerini isteyen ifadeye döner.</span><span class="sxs-lookup"><span data-stu-id="d2ced-118">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="d2ced-119">Sonlandırmak için gereklidir `If` .. `Then` . ...`Else` blok tanımı eşleşen bir ifade tarafından başlatıldı `If` .</span><span class="sxs-lookup"><span data-stu-id="d2ced-119">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="d2ced-120">Bkz [.... Sonra... Else bildirisi](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d2ced-120">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="d2ced-121">Eşleşen [arabirim bildirimiyle](interface-statement.md)başlatılan bir arabirim tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-121">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="d2ced-122">Eşleşen bir [Modül ifadesiyle](module-statement.md)başlatılan bir modül tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-122">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="d2ced-123">Bir ad alanı tanımını sonlandırmak için eşleşen bir [ad alanı ifadesiyle](namespace-statement.md)başlamış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-123">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="d2ced-124">Eşleşen [Işleç ifadesiyle](operator-statement.md)başlatılan bir operatör tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-124">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="d2ced-125">Eşleşen bir [özellik ifadesiyle](property-statement.md)başlatılan bir özellik tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-125">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="d2ced-126">`RaiseEvent` `RaiseEvent` Özel bir [olay deyimindeki](event-statement.md)eşleşen bir ifade tarafından başlatılan bir erişimciyi sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-126">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="d2ced-127">`RemoveHandler` `RemoveHandler` Özel bir [olay deyimindeki](event-statement.md)eşleşen bir ifade tarafından başlatılan bir erişimciyi sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-127">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="d2ced-128">`Select`Eşleşen bir deyimle başlatılan bir... `Case` Block tanımını sonlandırmak için gereklidir `Select` .</span><span class="sxs-lookup"><span data-stu-id="d2ced-128">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="d2ced-129">Bkz [. Select... Case bildirisi](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d2ced-129">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="d2ced-130">`Property`Eşleşen bir [küme ifadesiyle](set-statement.md)başlatılan bir yordam tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-130">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="d2ced-131">Yürütme bir `End Set` deyimle karşılaşırsa denetim, özelliğin değerini ayarlayarak ifadeye döner.</span><span class="sxs-lookup"><span data-stu-id="d2ced-131">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="d2ced-132">Eşleşen bir [Yapı bildirimiyle](structure-statement.md)başlatılan bir yapı tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-132">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="d2ced-133">`Sub`Eşleşen bir [Sub ifadesiyle](sub-statement.md)başlatılan bir yordam tanımını sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-133">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="d2ced-134">Yürütme bir `End Sub` deyimle karşılaşırsa, Denetim çağıran koda geri döner.</span><span class="sxs-lookup"><span data-stu-id="d2ced-134">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="d2ced-135">`SyncLock`Eşleşen bir deyimle başlatılan bir blok tanımını sonlandırmak için gereklidir `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="d2ced-135">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="d2ced-136">Bkz. [SyncLock bildirisi](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d2ced-136">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="d2ced-137">Sonlandırmak için gereklidir `Try` .. `Catch` . ...`Finally` blok tanımı eşleşen bir ifade tarafından başlatıldı `Try` .</span><span class="sxs-lookup"><span data-stu-id="d2ced-137">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="d2ced-138">Bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d2ced-138">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="d2ced-139">`While`Eşleşen bir deyimle başlatılan döngü tanımını sonlandırmak için gereklidir `While` .</span><span class="sxs-lookup"><span data-stu-id="d2ced-139">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="d2ced-140">Bkz.... [ End while bildirisi](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d2ced-140">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="d2ced-141">`With`Eşleşen bir deyimle başlatılan bir blok tanımını sonlandırmak için gereklidir `With` .</span><span class="sxs-lookup"><span data-stu-id="d2ced-141">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="d2ced-142">Bkz.... [ WITH Ifadesiyle biter](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d2ced-142">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="d2ced-143">Yönergeler</span><span class="sxs-lookup"><span data-stu-id="d2ced-143">Directives</span></span>

<span data-ttu-id="d2ced-144">Önünde bir sayı işareti () olduğunda `#` , `End` anahtar sözcüğü karşılık gelen yönerge tarafından tanıtılan bir ön işleme bloğunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d2ced-144">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="d2ced-145">Bölüm</span><span class="sxs-lookup"><span data-stu-id="d2ced-145">Part</span></span>|<span data-ttu-id="d2ced-146">Description</span><span class="sxs-lookup"><span data-stu-id="d2ced-146">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="d2ced-147">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-147">Required.</span></span> <span data-ttu-id="d2ced-148">Ön işleme bloğunun tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d2ced-148">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="d2ced-149">Bir dış kaynak bloğunu, eşleşen bir [#ExternalSource yönergesi](../directives/externalsource-directive.md)tarafından başlatılan sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-149">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="d2ced-150">Bir eşleşen yönergeyle başlatılan koşullu bir derleme bloğunu sonlandırmak için gereklidir `#If` .</span><span class="sxs-lookup"><span data-stu-id="d2ced-150">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="d2ced-151">Bkz [. #If... Sonra... #Else yönergeleri](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="d2ced-151">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="d2ced-152">Eşleşen bir [#Region yönergesi](../directives/region-directive.md)tarafından başlatılan bir kaynak bölgesi bloğunu sonlandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d2ced-152">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="d2ced-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2ced-153">Remarks</span></span>

<span data-ttu-id="d2ced-154">Ek anahtar sözcük olmadan [End ifadesinin](end-statement.md)yürütülmesi hemen sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d2ced-154">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="d2ced-155">Akıllı Cihaz Geliştirici Notları</span><span class="sxs-lookup"><span data-stu-id="d2ced-155">Smart Device Developer Notes</span></span>  

<span data-ttu-id="d2ced-156">`End`Ek bir anahtar sözcük olmadan ifade desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d2ced-156">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ced-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2ced-157">See also</span></span>

- [<span data-ttu-id="d2ced-158">End ekstresi</span><span class="sxs-lookup"><span data-stu-id="d2ced-158">End Statement</span></span>](end-statement.md)
