---
title: 'Nasıl yapılır: Bir Sabit Listesi Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 752b425ba32efe41a1ab1aa75de20039d36f5e50
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058904"
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="1357d-102">Nasıl yapılır: Numaralandırmaları Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1357d-102">How to: Declare Enumerations (Visual Basic)</span></span>

<span data-ttu-id="1357d-103">`Enum`Bir sınıfın veya modülün Bildirimler bölümünde ifadesiyle bir numaralandırma oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="1357d-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="1357d-104">Bir yöntem içinde bir numaralandırma bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1357d-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="1357d-105">Uygun erişim düzeyini belirtmek için,, veya kullanın `Private` `Protected` `Friend` `Public` .</span><span class="sxs-lookup"><span data-stu-id="1357d-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="1357d-106">Bir `Enum` tür, her biri bir sabiti temsil eden bir ad, temel tür ve bir alan kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="1357d-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="1357d-107">Ad geçerli bir .NET niteleyicisi olmalıdır Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1357d-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="1357d-108">Temel alınan tür tamsayı türlerinden biri olmalıdır — `Byte` , `Short` , `Long` veya `Integer` .</span><span class="sxs-lookup"><span data-stu-id="1357d-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="1357d-109">`Integer` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="1357d-109">`Integer` is the default.</span></span> <span data-ttu-id="1357d-110">Numaralandırmalar her zaman kesin olarak türlidir ve tamsayı sayı türleriyle birlikte değiştirilebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="1357d-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="1357d-111">Numaralandırmalar kayan nokta değerlerine sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="1357d-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="1357d-112">Bir numaralandırma ile bir kayan nokta değeri atanırsa bir `Option Strict On` derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="1357d-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="1357d-113">`Option Strict`İse `Off` , değer otomatik olarak `Enum` türüne dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="1357d-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="1357d-114">Adlar hakkında bilgi edinmek ve bu `Imports` deyimin ad nitelemesini gereksiz hale getirmek için nasıl kullanılacağını öğrenmek için bkz. [numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="1357d-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="1357d-115">Bir numaralandırma bildirmek için</span><span class="sxs-lookup"><span data-stu-id="1357d-115">To declare an enumeration</span></span>  
  
1. <span data-ttu-id="1357d-116">Her biri farklı bildiren bir kod erişim düzeyi, `Enum` anahtar sözcük ve geçerli bir ad içeren bir bildirim yazın `Enum` .</span><span class="sxs-lookup"><span data-stu-id="1357d-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. <span data-ttu-id="1357d-117">Sabit Listesi içindeki sabitleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1357d-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="1357d-118">Varsayılan olarak, bir Numaralandırmadaki ilk sabit olarak başlatılır `0` ve sonraki sabitler önceki sabitten bir değere başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1357d-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="1357d-119">Örneğin, aşağıdaki sabit listesi, `Days` değeri ile adlandırılmış bir sabit, değeri ile adlandırılmış bir sabit, `Sunday` `0` `Monday` `1` `Tuesday` ve değeri ile adlandırılmış `2` bir sabit içerir.</span><span class="sxs-lookup"><span data-stu-id="1357d-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. <span data-ttu-id="1357d-120">Atama ifadesini kullanarak, bir Numaralandırmadaki sabitlere açıkça değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1357d-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="1357d-121">Negatif sayılar da dahil olmak üzere herhangi bir tamsayı değeri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1357d-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="1357d-122">Örneğin, hata koşullarını temsil etmek için sıfırdan küçük değerler içeren sabitlerin olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1357d-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="1357d-123">Aşağıdaki numaralandırmada, sabit `Invalid` değere açıkça atanır `–1` ve sabit `Sunday` değere atanır `0` .</span><span class="sxs-lookup"><span data-stu-id="1357d-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="1357d-124">Numaralandırmadaki ilk sabit olduğundan, `Saturday` değer olarak da başlatılır `0` .</span><span class="sxs-lookup"><span data-stu-id="1357d-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="1357d-125">Değeri (değerinden `Monday` `1` bir daha fazla `Sunday` ); değeri `Tuesday` `2` , vb. olur.</span><span class="sxs-lookup"><span data-stu-id="1357d-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="1357d-126">Bir sabit listesini açık bir tür olarak bildirmek için</span><span class="sxs-lookup"><span data-stu-id="1357d-126">To declare an enumeration as an explicit type</span></span>  
  
- <span data-ttu-id="1357d-127">`As`Aşağıdaki örnekte gösterildiği gibi yan tümcesini kullanarak enum türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="1357d-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1357d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1357d-128">See also</span></span>

- [<span data-ttu-id="1357d-129">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="1357d-129">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="1357d-130">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="1357d-130">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="1357d-131">Nasıl yapılır: Visual Basic'de Numaralandırma Yoluyla Yineleme Yapma</span><span class="sxs-lookup"><span data-stu-id="1357d-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="1357d-132">Nasıl yapılır: Bir Numaralandırma Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="1357d-132">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="1357d-133">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="1357d-133">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="1357d-134">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1357d-134">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="1357d-135">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="1357d-135">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="1357d-136">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="1357d-136">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
