---
description: 'Hakkında daha fazla bilgi edinin: User-Defined sabitler (Visual Basic)'
title: Kullanıcı Tanımlı Sabitler
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 290d4122249315ae3c6dc5e18ca4faefecb72044
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485230"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="30d29-103">Kullanıcı Tanımlı Sabitler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30d29-103">User-Defined Constants (Visual Basic)</span></span>

<span data-ttu-id="30d29-104">Sabit, değişmez bir sayının veya dizenin yerini alan anlamlı bir addır.</span><span class="sxs-lookup"><span data-stu-id="30d29-104">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="30d29-105">Adın gösterdiği gibi sabitler depolama değerleri, bir uygulamanın yürütülmesi boyunca sabit kalır.</span><span class="sxs-lookup"><span data-stu-id="30d29-105">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="30d29-106">Üzerinde çalıştığınız denetimler veya bileşenler tarafından tanımlanan sabitleri kullanabilir veya kendi kendinize de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30d29-106">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="30d29-107">Kendi oluşturduğunuz sabitler *Kullanıcı tanımlı* olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="30d29-107">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="30d29-108">`Const`Bir değişken adı oluşturmak için kullandığınız yönergeleri kullanarak ifadesiyle bir sabit değeri bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30d29-108">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="30d29-109">`Option Strict`İse `On` , sabit türü açıkça bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="30d29-109">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="30d29-110">Const deyimin kullanımı</span><span class="sxs-lookup"><span data-stu-id="30d29-110">Const Statement Usage</span></span>  

 <span data-ttu-id="30d29-111">Bir `Const` ifade matematiksel veya tarih/saat sayısını temsil edebilir:</span><span class="sxs-lookup"><span data-stu-id="30d29-111">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="30d29-112">Ayrıca, sabitleri tanımlayabilir `String` :</span><span class="sxs-lookup"><span data-stu-id="30d29-112">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="30d29-113">Eşittir işaretinin () sağ tarafındaki ifade `=` genellikle bir sayı veya sabit dizedir, ancak aynı zamanda sayı veya dize ile sonuçlanan bir ifade da olabilir (Bu ifade işlevlere çağrılar içeremez).</span><span class="sxs-lookup"><span data-stu-id="30d29-113">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="30d29-114">Sabitleri, daha önce tanımlanmış sabitler bakımından bile tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30d29-114">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="30d29-115">User-Defined sabitleri kapsamı</span><span class="sxs-lookup"><span data-stu-id="30d29-115">Scope of User-Defined Constants</span></span>  

 <span data-ttu-id="30d29-116">Bir `Const` deyimin kapsamı aynı konumda bildirildiği bir değişkenle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="30d29-116">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="30d29-117">Kapsamı aşağıdaki yollarla belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30d29-117">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="30d29-118">Yalnızca bir yordamda var olan bir sabit oluşturmak için, bu yordamın içinde bildirin.</span><span class="sxs-lookup"><span data-stu-id="30d29-118">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="30d29-119">Bir sınıf içindeki tüm yordamlar için kullanılabilen, ancak bu modül dışındaki hiçbir koda yönelik bir sabit oluşturmak için, sınıfın Bildirimler bölümünde bildirin.</span><span class="sxs-lookup"><span data-stu-id="30d29-119">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="30d29-120">Bir derlemenin tüm üyeleri için kullanılabilen, ancak derlemenin dış istemcilerine yönelik bir sabit oluşturmak için, `Friend` sınıfının bildirimler bölümündeki anahtar sözcüğünü kullanarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="30d29-120">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="30d29-121">Uygulama genelinde kullanılabilir bir sabit oluşturmak için, `Public` sınıfının bildirimler bölümündeki anahtar sözcüğünü kullanarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="30d29-121">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="30d29-122">Daha fazla bilgi için bkz. [nasıl yapılır: bir sabit bildirme](how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="30d29-122">For more information, see [How to: Declare A Constant](how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="30d29-123">Döngüsel başvuruların kaçınma</span><span class="sxs-lookup"><span data-stu-id="30d29-123">Avoiding Circular References</span></span>  

 <span data-ttu-id="30d29-124">Sabitler diğer sabitler açısından tanımlanabileceğinden, iki veya daha fazla sabitler arasında yanlışlıkla bir *döngü* veya döngüsel başvuru oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="30d29-124">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="30d29-125">İki veya daha fazla ortak sabitiniz olduğunda, her biri diğeri farklı olduğunda, aşağıdaki örnekte olduğu gibi bir döngüden oluşur:</span><span class="sxs-lookup"><span data-stu-id="30d29-125">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="30d29-126">Bir döngüyle karşılaşırsanız Visual Basic bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30d29-126">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30d29-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30d29-127">See also</span></span>

- [<span data-ttu-id="30d29-128">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="30d29-128">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="30d29-129">Sabit ve Değişmez Değerli Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="30d29-129">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="30d29-130">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="30d29-130">Constants and Enumerations</span></span>](index.md)
- [<span data-ttu-id="30d29-131">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="30d29-131">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="30d29-132">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30d29-132">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="30d29-133">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30d29-133">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="30d29-134">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="30d29-134">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="30d29-135">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="30d29-135">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="30d29-136">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="30d29-136">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
