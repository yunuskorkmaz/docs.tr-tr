---
title: "Kullanıcı Tanımlı Sabitler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce839c3e843a52b31e40c13cb765f8eaf9959ea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="625a9-102">Kullanıcı Tanımlı Sabitler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="625a9-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="625a9-103">Bir sabit bir sayı veya değişmez dize yerini alır anlamlı bir addır.</span><span class="sxs-lookup"><span data-stu-id="625a9-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="625a9-104">Adından da anlaşılacağı gibi bir uygulama yürütme sabit kalır değerleri sabitleri depolar.</span><span class="sxs-lookup"><span data-stu-id="625a9-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="625a9-105">Denetimleri veya birlikte çalıştığınız bileşenleri tarafından tanımlanan sabitleri kullanabilir veya kendi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="625a9-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="625a9-106">Kendi başınıza oluşturduğunuz sabitleri olarak açıklanmıştır *kullanıcı tanımlı*.</span><span class="sxs-lookup"><span data-stu-id="625a9-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="625a9-107">İle bir sabit bildirme `Const` deyimi, bir değişken adı oluşturmak için yaptığınız aynı yönergeleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="625a9-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="625a9-108">Varsa `Option Strict` olan `On`, açıkça sabit türü belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="625a9-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="625a9-109">Const deyimi kullanımı</span><span class="sxs-lookup"><span data-stu-id="625a9-109">Const Statement Usage</span></span>  
 <span data-ttu-id="625a9-110">A `Const` deyimi bir matematik temsil veya tarih/saat miktarı:</span><span class="sxs-lookup"><span data-stu-id="625a9-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 <span data-ttu-id="625a9-111">Ayrıca tanımlayabilirsiniz `String` sabitleri:</span><span class="sxs-lookup"><span data-stu-id="625a9-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 <span data-ttu-id="625a9-112">Sağ tarafındaki ifade eşittir işaretinden ( `=` ) genellikle bir sayı veya değişmez değer dize olur, ancak (işlevlere çağrıları ifade içeremez rağmen), bir sayı veya dize sonuçları bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="625a9-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="625a9-113">Önceden tanımlanmış sabitleri bakımından sabitleri bile tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="625a9-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="625a9-114">Kullanıcı tanımlı sabitler kapsamı</span><span class="sxs-lookup"><span data-stu-id="625a9-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="625a9-115">A `Const` deyiminin kapsamı aynı konumda bildirilen bir değişken değil.</span><span class="sxs-lookup"><span data-stu-id="625a9-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="625a9-116">Kapsam aşağıdaki yollardan birini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="625a9-116">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="625a9-117">Yalnızca bir yordam içinde mevcut bir sabit oluşturmak için bu yordam içinde bildirin.</span><span class="sxs-lookup"><span data-stu-id="625a9-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="625a9-118">Bir sınıftaki tüm yordamlar ancak bu modül dışında herhangi bir kod için kullanılabilir bir sabit oluşturmak için sınıf bildirimleri bölümünde bildirin.</span><span class="sxs-lookup"><span data-stu-id="625a9-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="625a9-119">Bir derlemeyi tüm üyeleri ancak derlemenin dış istemciler için kullanılabilir bir sabit oluşturmak için kullanarak bildirme `Friend` sınıf bildirimleri bölümünde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="625a9-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="625a9-120">Uygulama genelinde kullanılabilir bir sabit oluşturmak için kullanarak bildirme `Public` anahtar sözcüğü bildirimlerden bölümünde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="625a9-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="625a9-121">Daha fazla bilgi için bkz: [nasıl yapılır: bir sabit bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="625a9-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="625a9-122">Döngüsel başvuru önleme</span><span class="sxs-lookup"><span data-stu-id="625a9-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="625a9-123">Sabitler diğer sabitleri bakımından tanımlanmış olması nedeniyle yanlışlıkla oluşturmak mümkün bir *döngüsü*, ya da iki veya daha fazla sabitler arasında döngüsel başvuru.</span><span class="sxs-lookup"><span data-stu-id="625a9-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="625a9-124">Diğer, aşağıdaki örnekte olduğu gibi bakımından tanımlanmış her biri iki veya daha fazla ortak sabitleri sahip olduğunda bir döngü oluşur:</span><span class="sxs-lookup"><span data-stu-id="625a9-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 <span data-ttu-id="625a9-125">Bir döngü ortaya çıkarsa, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="625a9-125">If a cycle occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="625a9-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="625a9-126">See Also</span></span>  
 [<span data-ttu-id="625a9-127">Const deyimi</span><span class="sxs-lookup"><span data-stu-id="625a9-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="625a9-128">Sabit ve değişmez değerli veri türleri</span><span class="sxs-lookup"><span data-stu-id="625a9-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="625a9-129">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="625a9-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [<span data-ttu-id="625a9-130">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="625a9-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="625a9-131">Numaralandırmalara genel bakış</span><span class="sxs-lookup"><span data-stu-id="625a9-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="625a9-132">Sabitlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="625a9-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="625a9-133">Nasıl yapılır: bir numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="625a9-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="625a9-134">Numaralandırmalar ve ad niteliği</span><span class="sxs-lookup"><span data-stu-id="625a9-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="625a9-135">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="625a9-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
