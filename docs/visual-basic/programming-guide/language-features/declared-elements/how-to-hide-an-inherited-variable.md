---
title: 'Nasıl yapılır: (Visual Basic) devralınmış değişkeni gizleme'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: 2b052b44043deba85c8b142a2bf1a684c1159809
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842518"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="5b7ef-102">Nasıl yapılır: (Visual Basic) devralınmış değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="5b7ef-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>
<span data-ttu-id="5b7ef-103">Türetilmiş bir sınıf kendi temel sınıfının tüm tanımları devralır.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="5b7ef-104">Bir öğe temel sınıf aynı adı kullanarak bir değişkeni tanımlamak istiyorsanız, gizleyebilirsiniz, veya *gölge*, türetilen sınıfta Değişkeninizi tanımladığınızda, temel sınıf öğesi.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="5b7ef-105">Bunu yaparsanız, türetilmiş sınıftaki kod açıkça gölgeleme mekanizması atlar sürece Değişkeninizi erişir.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>  
  
 <span data-ttu-id="5b7ef-106">Devralınmış değişkeni gizleme isteyebileceğiniz diğer bir neden, temel sınıf düzeltme karşı korunmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="5b7ef-107">Temel sınıf devralma öğe değiştiren bir değişiklik uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="5b7ef-108">Böyle bir durumda `Shadows` değiştiricisi değişkeninize, temel sınıf öğenin yerine çözülmesi türetilmiş sınıf başvurularından zorlar.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>  
  
### <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="5b7ef-109">Devralınmış değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="5b7ef-109">To hide an inherited variable</span></span>  
  
1.  <span data-ttu-id="5b7ef-110">Gizlemek istediğiniz değişken sınıf düzeyinde (dışında herhangi bir yordam) bildirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="5b7ef-111">Aksi takdirde gizlemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-111">Otherwise you do not need to hide it.</span></span>  
  
2.  <span data-ttu-id="5b7ef-112">Türetilmiş sınıf içinde yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) , değişken bildirme.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-112">Inside your derived class, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="5b7ef-113">Aynı ada, devralınmış değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-113">Use the same name as that of the inherited variable.</span></span>  
  
3.  <span data-ttu-id="5b7ef-114">Dahil [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) bildirimindeki anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-114">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="5b7ef-115">Türetilmiş sınıftaki kod değişken adıdır, derleyici Değişkeninizi başvuruyu çözümler.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="5b7ef-116">Aşağıdaki örnek, devralınan bir değişken gölgeleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-116">The following example illustrates shadowing of an inherited variable.</span></span>  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="5b7ef-117">Yukarıdaki örnekte değişkeni bildirir `shadowString` temel sınıf ve türetilen sınıfta gölgeliyor.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="5b7ef-118">Yordamı `showStrings` türetilmiş bir sınıf içindeki dize gölgeleme sürümünü görüntüler, ad `shadowString` yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-118">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="5b7ef-119">Ardından gölgeli sürüm görüntüler, `shadowString` ile tam olduğundan `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5b7ef-120">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="5b7ef-120">Robust Programming</span></span>  
 <span data-ttu-id="5b7ef-121">Gölgeleme, bir değişken aynı ada sahip birden fazla sürümünü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="5b7ef-122">Kod açıklaması değişken adıdır, derleyici başvurusu açığını giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="5b7ef-123">Bu gölgeli bir değişkenin istenmeyen bir sürüme başvuran riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="5b7ef-124">Bu riski tam olarak gölgeli bir değişken tüm başvurularını uygun tarafından düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b7ef-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b7ef-125">See also</span></span>

- [<span data-ttu-id="5b7ef-126">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="5b7ef-126">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="5b7ef-127">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="5b7ef-127">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="5b7ef-128">Gölgeleme ve Geçersiz Kılma Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="5b7ef-128">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="5b7ef-129">Nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="5b7ef-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="5b7ef-130">Nasıl yapılır: Türetilmiş sınıf tarafından gizlenen bir değişkene erişme</span><span class="sxs-lookup"><span data-stu-id="5b7ef-130">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="5b7ef-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="5b7ef-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="5b7ef-132">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="5b7ef-132">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="5b7ef-133">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="5b7ef-133">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
