---
title: 'Nasıl yapılır: Bir Sabit Bildirme (Visual Basic)'
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
ms.openlocfilehash: ce45e4df7f74cd68bde0fb2adba10197a11edb1b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394320"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="c2f4b-102">Nasıl yapılır: Bir Sabit Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2f4b-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="c2f4b-103">Kullandığınız `Const` deyimini bir sabit bildirme ve değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="c2f4b-104">Bir sabit bildirme tarafından bir değer anlamlı bir ad atayın.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="c2f4b-105">Bir sabit bildirildiğinde, değiştiren veya yeni bir değer atanır.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="c2f4b-106">Size, bir yordam içinde veya bir modül, sınıf veya yapı bildirimleri bölümünde bir sabit bildirme.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="c2f4b-107">Sınıf veya yapı düzeyi sabitleri `Private` , varsayılan olarak da bildirilmeleri ancak `Public`, `Friend`, `Protected`, veya `Protected Friend` uygun düzeyde kod erişim için.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="c2f4b-108">Sabit (kuralları değişken adları oluşturmak için aynıdır) geçerli bir simgesel ad ve sayısal veya dize sabitleri ve işleçler (ancak hiçbir işlev çağrıları) oluşan bir ifade olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="c2f4b-109">Bir sabit bildirme</span><span class="sxs-lookup"><span data-stu-id="c2f4b-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="c2f4b-110">Bir erişim belirticisi içeren bir bildirimi yazma `Const` anahtar sözcüğü ve aşağıdaki örneklerde gösterildiği gibi bir ifade:</span><span class="sxs-lookup"><span data-stu-id="c2f4b-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     <span data-ttu-id="c2f4b-111">Zaman [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) olduğu `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) olduğu `On`, bir veri türü belirterek bir sabiti açıkça bildirmelidir (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, veya `String`).</span><span class="sxs-lookup"><span data-stu-id="c2f4b-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="c2f4b-112">Zaman `Option Infer` olduğu `On` veya `Option Strict` olduğu `Off`, bir veri türüyle belirtmeden bir sabit bildirebilirsiniz bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="c2f4b-113">Derleyici sabiti ifadesinin türünden türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="c2f4b-114">Daha fazla bilgi için [sabit ve değişmez değer veri türleri](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="c2f4b-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="c2f4b-115">Açıkça belirtilen veri türü olan bir sabit bildirme</span><span class="sxs-lookup"><span data-stu-id="c2f4b-115">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="c2f4b-116">İçeren bir bildirimi yazma `As` anahtar sözcüğü ve açık bir veri türü, aşağıdaki örneklerde olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="c2f4b-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     <span data-ttu-id="c2f4b-117">Kodunuzu daha okunabilir her satırda yalnızca tek bir sabit bildirirseniz olmasına rağmen tek bir satırda birden çok sabitleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="c2f4b-118">Birden çok sabitleri tek bir satıra bildirirseniz, tümü aynı erişim düzeyini olmaları gerekir (`Public`, `Private`, `Friend`, `Protected`, veya `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="c2f4b-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="c2f4b-119">Birden çok sabitleri tek bir satıra bildirmek için</span><span class="sxs-lookup"><span data-stu-id="c2f4b-119">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="c2f4b-120">Bir virgül ve aşağıdaki örnekte olduğu gibi bir boşluk ile bildirimleri ayırın:</span><span class="sxs-lookup"><span data-stu-id="c2f4b-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c2f4b-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2f4b-121">See Also</span></span>  
 [<span data-ttu-id="c2f4b-122">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="c2f4b-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="c2f4b-123">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="c2f4b-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)  
 <span data-ttu-id="c2f4b-124">[Sabitlere genel bakış](constants-overview.md) [nasıl yapılır: bir sabit bildirme](how-to-declare-a-constant.md) [kullanıcı tanımlı sabitler](user-defined-constants.md) [sabit ve değişmez değerli veri türleri](constant-and-literal-data-types.md) [nasıl yapılır: Grup Sabit değerleri birlikte ilgili](how-to-group-related-constant-values-together.md) [numaralandırmalara genel bakış](enumerations-overview.md) [nasıl yapılır: numaralandırmaları bildirme](how-to-declare-enumerations.md) [nasıl yapılır: bir numaralandırma üyesine başvurma](how-to-refer-to-an-enumeration-member.md) [Numaralandırmalar ve ad niteliği](enumerations-and-name-qualification.md) [nasıl yapılır: bir sabit listesi yoluyla yineleme](how-to-iterate-through-an-enumeration.md) [nasıl yapılır: bir numaralandırma değeriyle ilişkili dizeyi belirleme](how-to-determine-the-string-associated-with-an-enumeration-value.md) [Bir numaralandırmanın ne zaman kullanılacağı](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="c2f4b-124">[Constants Overview](constants-overview.md) [How to: Declare A Constant](how-to-declare-a-constant.md) [User-Defined Constants](user-defined-constants.md) [Constant and Literal Data Types](constant-and-literal-data-types.md) [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md) [Enumerations Overview](enumerations-overview.md) [How to: Declare Enumerations](how-to-declare-enumerations.md) [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md) [Enumerations and Name Qualification](enumerations-and-name-qualification.md) [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md) [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md) [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 [<span data-ttu-id="c2f4b-125">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c2f4b-125">Enumerations Overview</span></span>](enumerations-overview.md)  
 [<span data-ttu-id="c2f4b-126">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c2f4b-126">Constants Overview</span></span>](constants-overview.md)  
 [<span data-ttu-id="c2f4b-127">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="c2f4b-127">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)  
 [<span data-ttu-id="c2f4b-128">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="c2f4b-128">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)  
 [<span data-ttu-id="c2f4b-129">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="c2f4b-129">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="c2f4b-130">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c2f4b-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
