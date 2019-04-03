---
title: 'Nasıl yapılır: (Visual Basic) bir sabit bildirme'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: 95bfa3da5499c518dad0c235b539784fee2bb522
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843415"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="67e55-102">Nasıl yapılır: (Visual Basic) bir sabit bildirme</span><span class="sxs-lookup"><span data-stu-id="67e55-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="67e55-103">Kullandığınız `Const` deyimini bir sabit bildirme ve değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="67e55-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="67e55-104">Bir sabit bildirme tarafından bir değer anlamlı bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="67e55-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="67e55-105">Bir sabit bildirildiğinde, değiştiren veya yeni bir değer atanır.</span><span class="sxs-lookup"><span data-stu-id="67e55-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="67e55-106">Size, bir yordam içinde veya bir modül, sınıf veya yapı bildirimleri bölümünde bir sabit bildirme.</span><span class="sxs-lookup"><span data-stu-id="67e55-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="67e55-107">Sınıf veya yapı düzeyi sabitleri `Private` , varsayılan olarak da bildirilmeleri ancak `Public`, `Friend`, `Protected`, veya `Protected Friend` uygun düzeyde kod erişim için.</span><span class="sxs-lookup"><span data-stu-id="67e55-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="67e55-108">Sabit (kuralları değişken adları oluşturmak için aynıdır) geçerli bir simgesel ad ve sayısal veya dize sabitleri ve işleçler (ancak hiçbir işlev çağrıları) oluşan bir ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="67e55-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="67e55-109">Bir sabit bildirme</span><span class="sxs-lookup"><span data-stu-id="67e55-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="67e55-110">Bir erişim belirticisi içeren bir bildirimi yazma `Const` anahtar sözcüğü ve aşağıdaki örneklerde gösterildiği gibi bir ifade:</span><span class="sxs-lookup"><span data-stu-id="67e55-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="67e55-111">Zaman [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) olduğu `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) olduğu `On`, bir veri türü belirterek bir sabiti açıkça bildirmelidir (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, veya `String`).</span><span class="sxs-lookup"><span data-stu-id="67e55-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="67e55-112">Zaman `Option Infer` olduğu `On` veya `Option Strict` olduğu `Off`, bir veri türüyle belirtmeden bir sabit bildirebilirsiniz bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="67e55-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="67e55-113">Derleyici sabiti ifadesinin türünden türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="67e55-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="67e55-114">Daha fazla bilgi için [sabit ve değişmez değer veri türleri](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="67e55-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="67e55-115">Açıkça belirtilen veri türü olan bir sabit bildirme</span><span class="sxs-lookup"><span data-stu-id="67e55-115">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="67e55-116">İçeren bir bildirimi yazma `As` anahtar sözcüğü ve açık bir veri türü, aşağıdaki örneklerde olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="67e55-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="67e55-117">Kodunuzu daha okunabilir her satırda yalnızca tek bir sabit bildirirseniz olmasına rağmen tek bir satırda birden çok sabitleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e55-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="67e55-118">Birden çok sabitleri tek bir satıra bildirirseniz, tümü aynı erişim düzeyini olmaları gerekir (`Public`, `Private`, `Friend`, `Protected`, veya `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="67e55-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="67e55-119">Birden çok sabitleri tek bir satıra bildirmek için</span><span class="sxs-lookup"><span data-stu-id="67e55-119">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="67e55-120">Bir virgül ve aşağıdaki örnekte olduğu gibi bir boşluk ile bildirimleri ayırın:</span><span class="sxs-lookup"><span data-stu-id="67e55-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="67e55-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e55-121">See also</span></span>

- [<span data-ttu-id="67e55-122">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="67e55-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="67e55-123">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="67e55-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="67e55-124">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="67e55-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="67e55-125">Nasıl yapılır: Bir sabit bildirme</span><span class="sxs-lookup"><span data-stu-id="67e55-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="67e55-126">Kullanıcı Tanımlı Sabitler</span><span class="sxs-lookup"><span data-stu-id="67e55-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="67e55-127">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="67e55-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="67e55-128">Nasıl yapılır: İlgili sabit değerleri birlikte gruplandırma</span><span class="sxs-lookup"><span data-stu-id="67e55-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="67e55-129">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="67e55-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="67e55-130">Nasıl yapılır: Sabit listesi bildirme</span><span class="sxs-lookup"><span data-stu-id="67e55-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="67e55-131">Nasıl yapılır: Bir numaralandırma üyesine başvurma</span><span class="sxs-lookup"><span data-stu-id="67e55-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="67e55-132">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="67e55-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="67e55-133">Nasıl yapılır: Bir sabit listesi yoluyla yineleme</span><span class="sxs-lookup"><span data-stu-id="67e55-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="67e55-134">Nasıl yapılır: Bir numaralandırma değeriyle ilişkili dizeyi belirleme</span><span class="sxs-lookup"><span data-stu-id="67e55-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="67e55-135">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="67e55-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="67e55-136">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="67e55-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="67e55-137">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="67e55-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="67e55-138">Nasıl yapılır: Bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="67e55-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="67e55-139">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="67e55-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="67e55-140">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="67e55-140">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="67e55-141">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="67e55-141">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
