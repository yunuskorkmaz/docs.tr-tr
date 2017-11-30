---
title: "Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3b2937cc71c0c31bd8dce3d77fb33f48e1b5750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="eaf6d-102">Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaf6d-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="eaf6d-103">Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak için kolay bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="eaf6d-104">Numaralandırma, bir ya da `Enum`, değer kümesi için bir simgesel ad.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="eaf6d-105">Numaralandırmalar veri türleri olarak kabul edilir ve değişkenleri ve özellikleri ile kullanım için sabitleri kümesi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="eaf6d-106">Bir Numaralandırmanın Ne Zaman Kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="eaf6d-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="eaf6d-107">Her bir yordam sınırlı sayıda değişkenleri kabul eder, numaralandırma kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="eaf6d-108">Özellikle anlamlı adları kullanıldığında numaralandırmalar NET ve daha okunabilir kodunu olun.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="eaf6d-109">Numaralandırmalar kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eaf6d-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="eaf6d-110">Sırasını değiştirme veya numaraları yanlış yazmanız kaynaklanan hataları azaltır.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="eaf6d-111">Gelecekte değerlerini değiştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="eaf6d-112">Hataları içine şekilde işi olasılığını anlamına gelen kod okumak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="eaf6d-113">İleriye dönük uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-113">Ensures forward compatibility.</span></span> <span data-ttu-id="eaf6d-114">Numaralandırmalar ile kodunuzu gelecekte birinin üyesi adlarına karşılık gelen değerleri değişirse başarısız daha az olasıdır.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="eaf6d-115">Numaralandırmalar adlandırma</span><span class="sxs-lookup"><span data-stu-id="eaf6d-115">Naming Enumerations</span></span>  
 <span data-ttu-id="eaf6d-116">Numaralandırma üyeleri için bir adlandırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="eaf6d-117">Zaman [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bir numaralandırma üye adı karşılaştığında diğer başvurulan tür kitaplıklarının aynı ada sahip olması durumunda bir özel durum oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-117">When [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="eaf6d-118">Uygulama veya bileşenin değerleri tanımlayan benzersiz bir ön ekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="eaf6d-119">Bir numaralandırma üyesi için söz konusu olduğunda, numaralandırma adıyla üye nitelemek veya desteklemeli kullanmak `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="eaf6d-120">Daha fazla bilgi için bkz: [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="eaf6d-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="eaf6d-121">Önceden tanımlanmış numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="eaf6d-121">Predefined Enumerations</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="eaf6d-122">önceden tanımlanmış numaralandırmalar sayısı gibi sağlar `FirstDayOfWeek` ve `MsgBoxResult`, kodunuzu kolaylaştırmak için.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-122"> provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="eaf6d-123">Bunların listesi için bkz: [sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="eaf6d-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf6d-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eaf6d-124">See Also</span></span>  
 [<span data-ttu-id="eaf6d-125">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="eaf6d-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="eaf6d-126">Nasıl yapılır: bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="eaf6d-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="eaf6d-127">Numaralandırmalar ve ad niteliği</span><span class="sxs-lookup"><span data-stu-id="eaf6d-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="eaf6d-128">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme</span><span class="sxs-lookup"><span data-stu-id="eaf6d-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="eaf6d-129">Nasıl yapılır: bir numaralandırma değeriyle ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="eaf6d-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="eaf6d-130">Enum deyimi</span><span class="sxs-lookup"><span data-stu-id="eaf6d-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="eaf6d-131">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="eaf6d-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
