---
title: "Nasıl yapılır: Devralınmış Değişkeni Gizleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2059da873f8b9ec9ea51191139c652a9e01d92b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="5cf21-102">Nasıl yapılır: Devralınmış Değişkeni Gizleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cf21-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>
<span data-ttu-id="5cf21-103">Türetilmiş bir sınıf kendi temel sınıfının tüm tanımları devralır.</span><span class="sxs-lookup"><span data-stu-id="5cf21-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="5cf21-104">Bir temel sınıf öğesi olarak aynı adı taşıyan bir değişkeni tanımlamak istiyorsanız, gizleyebilirsiniz, veya *gölge*, türetilen sınıfta değişkeniniz tanımladığınızda, temel sınıf öğesi.</span><span class="sxs-lookup"><span data-stu-id="5cf21-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="5cf21-105">Bunu yaparsanız, türetilmiş sınıf kodda açıkça gölgeleme mekanizması atlar sürece değişkeniniz erişir.</span><span class="sxs-lookup"><span data-stu-id="5cf21-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>  
  
 <span data-ttu-id="5cf21-106">Başka bir nedenle devralınmış değişkeni gizleme isteyebilirsiniz, temel sınıf düzeltme karşı korumaktır.</span><span class="sxs-lookup"><span data-stu-id="5cf21-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="5cf21-107">Taban sınıf devralma öğesi olarak değiştiren bir değişiklik uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5cf21-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="5cf21-108">Bu durumda, `Shadows` değiştiricisi değişkeniniz için temel sınıf öğesine yerine çözülmesi türetilmiş sınıf başvurularından zorlar.</span><span class="sxs-lookup"><span data-stu-id="5cf21-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>  
  
### <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="5cf21-109">Devralınmış değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="5cf21-109">To hide an inherited variable</span></span>  
  
1.  <span data-ttu-id="5cf21-110">Gizlemek istediğiniz değişkeni (dışında herhangi bir yordam) Sınıf düzeyinde bildirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5cf21-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="5cf21-111">Aksi takdirde gizleme gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5cf21-111">Otherwise you do not need to hide it.</span></span>  
  
2.  <span data-ttu-id="5cf21-112">Türetilmiş sınıf içinde yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) , değişken bildirme.</span><span class="sxs-lookup"><span data-stu-id="5cf21-112">Inside your derived class, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="5cf21-113">Aynı adı, devralınmış değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cf21-113">Use the same name as that of the inherited variable.</span></span>  
  
3.  <span data-ttu-id="5cf21-114">Dahil [gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md) bildiriminde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5cf21-114">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="5cf21-115">Türetilmiş sınıf kodda değişken adına başvurduğunda, derleyici, değişkeni referansı çözümler.</span><span class="sxs-lookup"><span data-stu-id="5cf21-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="5cf21-116">Aşağıdaki örnek devralınmış değişkeni gölgeleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cf21-116">The following example illustrates shadowing of an inherited variable.</span></span>  
  
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
  
     <span data-ttu-id="5cf21-117">Önceki örnekte değişken bildirir `shadowString` temel sınıf ve türetilen sınıfta shadows.</span><span class="sxs-lookup"><span data-stu-id="5cf21-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="5cf21-118">Yordamı `showStrings` türetilen sınıfta dize gölgeleme sürümünü görüntüler zaman adı `shadowString` yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="5cf21-118">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="5cf21-119">Ardından gölgeli sürümünü görüntüler zaman `shadowString` ile nitelenmiş `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5cf21-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5cf21-120">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="5cf21-120">Robust Programming</span></span>  
 <span data-ttu-id="5cf21-121">Gölgeleme aynı ada sahip bir değişken birden fazla sürümünü getirmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cf21-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="5cf21-122">Kod açıklaması değişken adına başvurduğunda, derleyici Başvurusu Güvenlik giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi etkenlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5cf21-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="5cf21-123">Bu gölgeli bir değişken istenmeyen bir sürümüne başvuran riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="5cf21-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="5cf21-124">Bu riski tam olarak gölgeli bir değişken yapılan tüm başvuruları niteleme tarafından düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cf21-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf21-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cf21-125">See Also</span></span>  
 [<span data-ttu-id="5cf21-126">Bildirilmiş öğelere başvurular</span><span class="sxs-lookup"><span data-stu-id="5cf21-126">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="5cf21-127">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="5cf21-127">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="5cf21-128">Gölgeleme ve geçersiz kılma arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="5cf21-128">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="5cf21-129">Nasıl yapılır: değişkeninizle aynı ada sahip bir değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="5cf21-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [<span data-ttu-id="5cf21-130">Nasıl yapılır: türetilmiş sınıf tarafından gizlenen bir değişkene erişme</span><span class="sxs-lookup"><span data-stu-id="5cf21-130">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [<span data-ttu-id="5cf21-131">Geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="5cf21-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="5cf21-132">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="5cf21-132">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="5cf21-133">Devralma temelleri</span><span class="sxs-lookup"><span data-stu-id="5cf21-133">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
