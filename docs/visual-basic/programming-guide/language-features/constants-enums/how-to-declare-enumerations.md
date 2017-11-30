---
title: "Nasıl yapılır: Numaralandırmaları Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 938550ebbfcf099729db3de96b809549cb234d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="beb94-102">Nasıl yapılır: Numaralandırmaları Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="beb94-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="beb94-103">Bir numaralandırma ile oluşturduğunuz `Enum` deyiminin bildirimleri bölümünde bir sınıf veya modülü.</span><span class="sxs-lookup"><span data-stu-id="beb94-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="beb94-104">Bir yöntem içinde bir numaralandırmayı bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="beb94-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="beb94-105">Uygun erişim düzeyini belirtmek için kullanın `Private`, `Protected`, `Friend`, veya `Public`.</span><span class="sxs-lookup"><span data-stu-id="beb94-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="beb94-106">Bir `Enum` türüne sahip bir ad, bir temel alınan türü ve bir dizi alanları, her bir sabiti temsil eden.</span><span class="sxs-lookup"><span data-stu-id="beb94-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="beb94-107">Ad geçerli bir Visual Basic .NET niteleyici olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="beb94-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="beb94-108">Temel alınan tür tamsayı türlerden biri olmalıdır:`Byte`, `Short`, `Long` veya `Integer`.</span><span class="sxs-lookup"><span data-stu-id="beb94-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="beb94-109">`Integer`varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="beb94-109">`Integer` is the default.</span></span> <span data-ttu-id="beb94-110">Numaralandırmalar her zaman kesin türü belirtilmiş ve tamsayı türle birbirinin yerine geçemez.</span><span class="sxs-lookup"><span data-stu-id="beb94-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="beb94-111">Numaralandırmalar kayan nokta değerlerine sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="beb94-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="beb94-112">Kayan nokta değeri olan bir numaralandırma atanmışsa `Option Strict On`, derleyici hatası sonuçları.</span><span class="sxs-lookup"><span data-stu-id="beb94-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="beb94-113">Varsa `Option Strict` olan `Off`, değer otomatik olarak dönüştürülür `Enum` türü.</span><span class="sxs-lookup"><span data-stu-id="beb94-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="beb94-114">Adları hakkında bilgi ve nasıl kullanılacağını `Imports` ad niteliği gereksiz, yapmak için Bildirimi'ne [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="beb94-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="beb94-115">Bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="beb94-115">To declare an enumeration</span></span>  
  
1.  <span data-ttu-id="beb94-116">Kod erişim düzeyi içeren bir bildirim yazma `Enum` anahtar sözcüğü ve her biri farklı bir bildirir geçerli bir ad, aşağıdaki örneklerde olduğu gibi `Enum`.</span><span class="sxs-lookup"><span data-stu-id="beb94-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  <span data-ttu-id="beb94-117">Sabitler numaralandırmada tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="beb94-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="beb94-118">Varsayılan olarak, bir listedeki ilk sabiti için başlatılmış `0`, ve sonraki sabitleri önceki sabiti'den fazla bir değere başlatılır.</span><span class="sxs-lookup"><span data-stu-id="beb94-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="beb94-119">Örneğin, aşağıdaki numaralandırması `Days`, adlandırılmış bir sabit içeriyor `Sunday` değerle `0`, adlı bir sabit `Monday` değerle `1`, adlı bir sabit `Tuesday` değeriyle`2`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="beb94-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  <span data-ttu-id="beb94-120">Değerler numaralandırma sabitler için bir atama deyimi kullanılarak açıkça atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beb94-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="beb94-121">Negatif sayılar dahil olmak üzere, herhangi bir tamsayı değeri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beb94-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="beb94-122">Örneğin, hata koşullarını temsil etmek için sıfır'den az olan değerlerin ile sabitleri isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beb94-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="beb94-123">Aşağıdaki listedeki sabiti `Invalid` değeri açıkça atanan `–1`ve sabit `Sunday` değeri atanmış `0`.</span><span class="sxs-lookup"><span data-stu-id="beb94-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="beb94-124">Listedeki ilk sabit olduğundan `Saturday` değerine de başlatılır `0`.</span><span class="sxs-lookup"><span data-stu-id="beb94-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="beb94-125">Değeri `Monday` olan `1` (tane değerinden daha `Sunday`); değerini `Tuesday` olan `2`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="beb94-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="beb94-126">Sabit açık bir tür olarak bildirmek için</span><span class="sxs-lookup"><span data-stu-id="beb94-126">To declare an enumeration as an explicit type</span></span>  
  
-   <span data-ttu-id="beb94-127">Enum türü kullanarak belirtin `As` aşağıdaki örnekte gösterildiği gibi yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="beb94-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="beb94-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="beb94-128">See Also</span></span>  
 [<span data-ttu-id="beb94-129">Numaralandırmalar ve ad niteliği</span><span class="sxs-lookup"><span data-stu-id="beb94-129">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="beb94-130">Nasıl yapılır: bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="beb94-130">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="beb94-131">Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme</span><span class="sxs-lookup"><span data-stu-id="beb94-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="beb94-132">Nasıl yapılır: bir numaralandırma değeriyle ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="beb94-132">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="beb94-133">Bir numaralandırmanın ne zaman kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="beb94-133">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="beb94-134">Sabitlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="beb94-134">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="beb94-135">Sabit ve değişmez değerli veri türleri</span><span class="sxs-lookup"><span data-stu-id="beb94-135">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="beb94-136">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="beb94-136">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
