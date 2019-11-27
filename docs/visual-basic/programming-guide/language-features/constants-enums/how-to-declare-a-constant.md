---
title: 'Nasıl yapılır: Bir Sabit Bildirme'
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
ms.openlocfilehash: 5054d4a4fc02d8bd22efceb01770fc54167d8cb3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347467"
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="c67d6-102">Nasıl yapılır: Bir Sabit Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c67d6-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="c67d6-103">Bir sabiti bildirmek ve değerini ayarlamak için `Const` ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c67d6-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="c67d6-104">Bir sabiti bildirerek, bir değere anlamlı bir ad atarsınız.</span><span class="sxs-lookup"><span data-stu-id="c67d6-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="c67d6-105">Sabit bir kez bildirildiğinde, değiştirilemez veya yeni bir değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="c67d6-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="c67d6-106">Bir yordamın içinde veya bir modülün, sınıfın veya yapının Bildirimler bölümünde bir sabit değer bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c67d6-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="c67d6-107">Sınıf veya yapı düzeyi sabitleri varsayılan olarak `Private`, ancak uygun kod erişimi düzeyi için `Public`, `Friend`, `Protected`veya `Protected Friend` olarak da belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c67d6-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="c67d6-108">Sabit, geçerli bir sembolik ada sahip olmalıdır (kurallar, değişken adları oluşturanlarla aynıdır) ve sayısal veya dize sabitleri ve işleçlerden oluşan bir ifade (ancak işlev çağrısı yoktur).</span><span class="sxs-lookup"><span data-stu-id="c67d6-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="c67d6-109">Bir sabit bildirmek için</span><span class="sxs-lookup"><span data-stu-id="c67d6-109">To declare a constant</span></span>  
  
- <span data-ttu-id="c67d6-110">Aşağıdaki örneklerde olduğu gibi, bir erişim belirticisi, `Const` anahtar sözcüğü ve bir ifade içeren bir bildirim yazın:</span><span class="sxs-lookup"><span data-stu-id="c67d6-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#8)]  
  
     <span data-ttu-id="c67d6-111">[Seçenek çıkarımı](../../../../visual-basic/language-reference/statements/option-infer-statement.md) `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) `On`, bir veri türü (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`veya `String`) belirterek bir sabiti açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c67d6-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="c67d6-112">`Option Infer` `On` veya `Option Strict` `Off`olduğunda, bir `As` yan tümcesiyle veri türü belirtmeden bir sabit bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c67d6-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="c67d6-113">Derleyici, ifadenin türünden sabit türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="c67d6-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="c67d6-114">Daha fazla bilgi için bkz. [sabit ve değişmez değerli veri türleri](constant-and-literal-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="c67d6-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="c67d6-115">Açıkça belirtilen bir veri türüne sahip bir sabit bildirmek için</span><span class="sxs-lookup"><span data-stu-id="c67d6-115">To declare a constant that has an explicitly stated data type</span></span>  
  
- <span data-ttu-id="c67d6-116">Aşağıdaki örneklerde olduğu gibi `As` anahtar sözcüğünü ve açık bir veri türünü içeren bir bildirim yazın:</span><span class="sxs-lookup"><span data-stu-id="c67d6-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#9)]  
  
     <span data-ttu-id="c67d6-117">Her satırda yalnızca tek bir sabit değer bildirirseniz kodunuz daha okunabilir olsa da, tek bir satırda birden çok sabit bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c67d6-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="c67d6-118">Tek bir satırda birden çok sabit bildirirseniz, tümünün aynı erişim düzeyine sahip olmaları gerekir (`Public`, `Private`, `Friend`, `Protected`veya `Protected Friend`).</span><span class="sxs-lookup"><span data-stu-id="c67d6-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="c67d6-119">Birden çok sabiti tek bir satırda bildirmek için</span><span class="sxs-lookup"><span data-stu-id="c67d6-119">To declare multiple constants on a single line</span></span>  
  
- <span data-ttu-id="c67d6-120">Aşağıdaki örnekte olduğu gibi, bildirimleri virgülle ve boşlukla ayırın:</span><span class="sxs-lookup"><span data-stu-id="c67d6-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```vb  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c67d6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c67d6-121">See also</span></span>

- [<span data-ttu-id="c67d6-122">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="c67d6-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="c67d6-123">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="c67d6-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="c67d6-124">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c67d6-124">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="c67d6-125">Nasıl yapılır: Bir Sabit Bildirme</span><span class="sxs-lookup"><span data-stu-id="c67d6-125">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="c67d6-126">Kullanıcı Tanımlı Sabitler</span><span class="sxs-lookup"><span data-stu-id="c67d6-126">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="c67d6-127">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="c67d6-127">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="c67d6-128">Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="c67d6-128">How to: Group Related Constant Values Together</span></span>](how-to-group-related-constant-values-together.md)
- [<span data-ttu-id="c67d6-129">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c67d6-129">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="c67d6-130">Nasıl yapılır: Bir Sabit Listesi Bildirme</span><span class="sxs-lookup"><span data-stu-id="c67d6-130">How to: Declare Enumerations</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="c67d6-131">Nasıl yapılır: Bir Sabit Listesi Üyesine Başvurma</span><span class="sxs-lookup"><span data-stu-id="c67d6-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="c67d6-132">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="c67d6-132">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="c67d6-133">Nasıl yapılır: Sabit Listesi Yoluyla Yineleme</span><span class="sxs-lookup"><span data-stu-id="c67d6-133">How to: Iterate Through An Enumeration</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="c67d6-134">Nasıl yapılır: Bir Sabit Listesi Değeriyle İlişkili Dizeyi Belirleme</span><span class="sxs-lookup"><span data-stu-id="c67d6-134">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="c67d6-135">Sabit Listesi Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="c67d6-135">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)

- [<span data-ttu-id="c67d6-136">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c67d6-136">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="c67d6-137">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c67d6-137">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="c67d6-138">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="c67d6-138">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="c67d6-139">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="c67d6-139">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="c67d6-140">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="c67d6-140">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c67d6-141">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c67d6-141">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
