---
title: Bir Numaralandırmanın Ne Zaman Kullanılacağı
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 7b1b269a5d28d89cd491bac88fbefd4547fdc3c3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095635"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="a44b6-102">Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a44b6-102">When to Use an Enumeration (Visual Basic)</span></span>

<span data-ttu-id="a44b6-103">Numaralandırmalar ilgili sabitler kümesiyle çalışmanın kolay bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="a44b6-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="a44b6-104">Bir sabit listesi veya `Enum` , bir değer kümesi için sembolik bir addır.</span><span class="sxs-lookup"><span data-stu-id="a44b6-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="a44b6-105">Numaralandırmalar veri türleri olarak değerlendirilir ve bunları, değişkenler ve özelliklerle kullanılacak sabitler kümesi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a44b6-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="a44b6-106">Bir Numaralandırmanın Ne Zaman Kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="a44b6-106">When to Use an Enumeration</span></span>  

 <span data-ttu-id="a44b6-107">Her bir yordam sınırlı bir değişken kümesini kabul ettiğinde, bir numaralandırma kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="a44b6-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="a44b6-108">Numaralandırmalar, özellikle anlamlı adlar kullanıldığında daha net ve daha okunabilir kod için yapılır.</span><span class="sxs-lookup"><span data-stu-id="a44b6-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="a44b6-109">Numaralandırmalar kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a44b6-109">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="a44b6-110">Dışarı veya hatalı yazma numaralarının neden olduğu hataları azaltır.</span><span class="sxs-lookup"><span data-stu-id="a44b6-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="a44b6-111">Gelecekte değerlerin değiştirilmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a44b6-111">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="a44b6-112">Kodu daha kolay okunabilir hale getirir, yani hataların buna katması daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="a44b6-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="a44b6-113">İleriye dönük uyumluluğu sağlar.</span><span class="sxs-lookup"><span data-stu-id="a44b6-113">Ensures forward compatibility.</span></span> <span data-ttu-id="a44b6-114">Numaralandırmalar sayesinde, gelecekte birisi üye adlarına karşılık gelen değerleri değiştirirse kodunuzun başarısız olma olasılığı düşüktür.</span><span class="sxs-lookup"><span data-stu-id="a44b6-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="a44b6-115">Sabit listeleri adlandırma</span><span class="sxs-lookup"><span data-stu-id="a44b6-115">Naming Enumerations</span></span>  

 <span data-ttu-id="a44b6-116">Numaralandırma üyeleri için bir adlandırma kuralı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a44b6-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="a44b6-117">Visual Basic bir numaralandırma üye adıyla karşılaştığında, başvurulan diğer tür kitaplıkları aynı adı içeriyorsa bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="a44b6-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="a44b6-118">Uygulamanızdan veya bileşeninizden değerleri tanımlayan benzersiz bir ön ek kullanın.</span><span class="sxs-lookup"><span data-stu-id="a44b6-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="a44b6-119">Bir numaralandırmanın üyesine başvuru yaparken, üye adını numaralandırma adıyla nitelemeniz veya daha sonra ifadesini kullanmanız gerekir `Imports` .</span><span class="sxs-lookup"><span data-stu-id="a44b6-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="a44b6-120">Daha fazla bilgi için bkz. [numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="a44b6-120">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="a44b6-121">Önceden tanımlanmış numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="a44b6-121">Predefined Enumerations</span></span>  

 <span data-ttu-id="a44b6-122">Visual Basic, `FirstDayOfWeek` kodunuzu kolaylaştırmak için ve gibi bir dizi önceden tanımlanmış sabit listesi sağlar `MsgBoxResult` .</span><span class="sxs-lookup"><span data-stu-id="a44b6-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="a44b6-123">Bunların bir listesi için bkz. [sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="a44b6-123">For a list of these see [Constants and Enumerations](../../../language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44b6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a44b6-124">See also</span></span>

- [<span data-ttu-id="a44b6-125">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="a44b6-125">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="a44b6-126">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="a44b6-126">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="a44b6-127">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="a44b6-127">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="a44b6-128">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="a44b6-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="a44b6-129">Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="a44b6-129">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="a44b6-130">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="a44b6-130">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="a44b6-131">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="a44b6-131">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
