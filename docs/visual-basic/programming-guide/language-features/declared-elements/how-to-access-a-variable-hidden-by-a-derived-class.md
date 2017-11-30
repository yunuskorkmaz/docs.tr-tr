---
title: "Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f94e45fcb0a26b0d59789e101c37aceba219250
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="3d536-102">Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d536-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>
<span data-ttu-id="3d536-103">Türetilmiş bir sınıf kodda bir değişken eriştiğinde derleyici sürümüne başvuru en yakın erişilebilir, diğer bir deyişle, erişilebilir sürümü en az derivational adımları geriye dönük erişilirken sınıfından normalde çözümler.</span><span class="sxs-lookup"><span data-stu-id="3d536-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="3d536-104">Değişkeni türetilmiş sınıfında tanımlanmışsa kodu tanımın normal olarak erişir.</span><span class="sxs-lookup"><span data-stu-id="3d536-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>  
  
 <span data-ttu-id="3d536-105">Türetilmiş sınıf değişkeni temel sınıfı bir değişkende shadows, temel sınıf sürüm gizler.</span><span class="sxs-lookup"><span data-stu-id="3d536-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="3d536-106">İle niteleme tarafından temel sınıf değişkenine ancak erişebilir `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="3d536-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="3d536-107">Türetilmiş sınıf tarafından gizlenen bir temel sınıf değişkene erişmek için</span><span class="sxs-lookup"><span data-stu-id="3d536-107">To access a base class variable hidden by a derived class</span></span>  
  
-   <span data-ttu-id="3d536-108">Bir deyim veya atama deyimi değişken adından `MyBase` anahtar sözcüğü ve bir süre (`.`).</span><span class="sxs-lookup"><span data-stu-id="3d536-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>  
  
     <span data-ttu-id="3d536-109">Derleyici değişkenin temel sınıf sürümüne başvuru çözümler.</span><span class="sxs-lookup"><span data-stu-id="3d536-109">The compiler resolves the reference to the base class version of the variable.</span></span>  
  
     <span data-ttu-id="3d536-110">Aşağıdaki örnek, devralma yoluyla gölgeleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d536-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="3d536-111">İki başvuru, gölgeleme değişkeni erişen diğeri gölgeleme atlayan kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3d536-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="3d536-112">Önceki örnekte değişken bildirir `shadowString` temel sınıf ve türetilen sınıfta shadows.</span><span class="sxs-lookup"><span data-stu-id="3d536-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="3d536-113">Yordamı `showStrings` türetilen sınıfta dize gölgeleme sürümünü görüntüler zaman adı `shadowString` yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="3d536-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="3d536-114">Ardından gölgeli sürümünü görüntüler zaman `shadowString` ile nitelenmiş `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="3d536-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3d536-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="3d536-115">Robust Programming</span></span>  
 <span data-ttu-id="3d536-116">Gölgeli bir değişken istenmeyen bir sürümüne başvuran riskini düşürmek için tüm başvurular gölgeli bir değişkene tam olarak nitelemek.</span><span class="sxs-lookup"><span data-stu-id="3d536-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="3d536-117">Gölgeleme aynı ada sahip bir değişken birden fazla sürümünü getirmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d536-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="3d536-118">Kod açıklaması değişken adına başvurduğunda, derleyici Başvurusu Güvenlik giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi etkenlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3d536-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="3d536-119">Bu değişkeni yanlış sürüme başvuran riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="3d536-119">This can increase the risk of referring to the wrong version of the variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d536-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d536-120">See Also</span></span>  
 [<span data-ttu-id="3d536-121">Bildirilmiş öğelere başvurular</span><span class="sxs-lookup"><span data-stu-id="3d536-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="3d536-122">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="3d536-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="3d536-123">Gölgeleme ve geçersiz kılma arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="3d536-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [<span data-ttu-id="3d536-124">Nasıl yapılır: değişkeninizle aynı ada sahip bir değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="3d536-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [<span data-ttu-id="3d536-125">Nasıl yapılır: devralınmış değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="3d536-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [<span data-ttu-id="3d536-126">Gölgeleri</span><span class="sxs-lookup"><span data-stu-id="3d536-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="3d536-127">Geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="3d536-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="3d536-128">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="3d536-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="3d536-129">Devralma temelleri</span><span class="sxs-lookup"><span data-stu-id="3d536-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
