---
title: Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ab152687f4f9e4ba6bd032ae7c1352f65af715f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="c1d0f-102">Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1d0f-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="c1d0f-103">Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak için kolay bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="c1d0f-104">Numaralandırma, bir ya da `Enum`, değer kümesi için bir simgesel ad.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="c1d0f-105">Numaralandırmalar veri türleri olarak kabul edilir ve değişkenleri ve özellikleri ile kullanım için sabitleri kümesi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="c1d0f-106">Bir Numaralandırmanın Ne Zaman Kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="c1d0f-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="c1d0f-107">Her bir yordam sınırlı sayıda değişkenleri kabul eder, numaralandırma kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="c1d0f-108">Özellikle anlamlı adları kullanıldığında numaralandırmalar NET ve daha okunabilir kodunu olun.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="c1d0f-109">Numaralandırmalar kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c1d0f-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="c1d0f-110">Sırasını değiştirme veya numaraları yanlış yazmanız kaynaklanan hataları azaltır.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="c1d0f-111">Gelecekte değerlerini değiştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="c1d0f-112">Hataları içine şekilde işi olasılığını anlamına gelen kod okumak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="c1d0f-113">İleriye dönük uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-113">Ensures forward compatibility.</span></span> <span data-ttu-id="c1d0f-114">Numaralandırmalar ile kodunuzu gelecekte birinin üyesi adlarına karşılık gelen değerleri değişirse başarısız daha az olasıdır.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="c1d0f-115">Numaralandırmalar adlandırma</span><span class="sxs-lookup"><span data-stu-id="c1d0f-115">Naming Enumerations</span></span>  
 <span data-ttu-id="c1d0f-116">Numaralandırma üyeleri için bir adlandırma kuralını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="c1d0f-117">Visual Basic bir numaralandırma üye adı karşılaştığında, diğer başvurulan tür kitaplıklarının aynı ada sahip olması durumunda bir özel durum oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="c1d0f-118">Uygulama veya bileşenin değerleri tanımlayan benzersiz bir ön ekini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="c1d0f-119">Bir numaralandırma üyesi için söz konusu olduğunda, numaralandırma adıyla üye nitelemek veya desteklemeli kullanmak `Imports` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="c1d0f-120">Daha fazla bilgi için bkz: [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="c1d0f-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="c1d0f-121">Önceden tanımlanmış numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c1d0f-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="c1d0f-122">Visual Basic sağlayan bir dizi önceden tanımlanmış numaralandırmalar gibi `FirstDayOfWeek` ve `MsgBoxResult`, kodunuzu kolaylaştırmak için.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="c1d0f-123">Bunların listesi için bkz: [sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="c1d0f-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d0f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1d0f-124">See Also</span></span>  
 [<span data-ttu-id="c1d0f-125">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="c1d0f-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="c1d0f-126">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="c1d0f-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="c1d0f-127">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="c1d0f-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="c1d0f-128">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme</span><span class="sxs-lookup"><span data-stu-id="c1d0f-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="c1d0f-129">Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="c1d0f-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="c1d0f-130">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="c1d0f-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="c1d0f-131">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c1d0f-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
