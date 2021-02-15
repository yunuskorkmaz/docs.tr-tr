---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme (Visual Basic)'
title: 'Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 5ac1dd8afc8c32c91b748c8316d035d69468d887
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430059"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="1d41d-103">Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d41d-103">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="1d41d-104">Türetilmiş bir sınıftaki kod bir değişkene eriştiğinde, derleyici normal olarak en yakın erişilebilen sürüme (diğer bir deyişle, erişim sınıfından geri doğru olan erişilebilir sürüme) başvuruyu çözümler.</span><span class="sxs-lookup"><span data-stu-id="1d41d-104">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="1d41d-105">Değişken türetilmiş sınıfta tanımlanmışsa, kod normalde bu tanıma erişir.</span><span class="sxs-lookup"><span data-stu-id="1d41d-105">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="1d41d-106">Türetilmiş sınıf değişkeni, temel sınıftaki bir değişkeni göltiği takdirde, temel sınıf sürümünü gizler.</span><span class="sxs-lookup"><span data-stu-id="1d41d-106">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="1d41d-107">Ancak, anahtar sözcüğü ile niteleyerek temel sınıf değişkenine erişebilirsiniz `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="1d41d-107">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="1d41d-108">Türetilmiş bir sınıf tarafından gizlenen bir taban sınıf değişkenine erişmek için</span><span class="sxs-lookup"><span data-stu-id="1d41d-108">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="1d41d-109">Bir ifade veya atama deyiminde, değişken adından önce `MyBase` anahtar sözcüğü ve nokta ( `.` ) koyun.</span><span class="sxs-lookup"><span data-stu-id="1d41d-109">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="1d41d-110">Derleyici, değişkenin temel sınıf sürümüne başvuruyu çözer.</span><span class="sxs-lookup"><span data-stu-id="1d41d-110">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="1d41d-111">Aşağıdaki örnek, devralma yoluyla gölgelendirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d41d-111">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="1d41d-112">Biri, gölgeleme değişkenine erişen diğeri de gölgelendirmeyi atlayan iki başvuru yapar.</span><span class="sxs-lookup"><span data-stu-id="1d41d-112">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
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

    <span data-ttu-id="1d41d-113">Önceki örnek, değişkeni `shadowString` temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri.</span><span class="sxs-lookup"><span data-stu-id="1d41d-113">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="1d41d-114">`showStrings`Türetilmiş sınıftaki yordamda, ad uygun olmadığında dizenin gölgeleme sürümü görüntülenir `shadowString` .</span><span class="sxs-lookup"><span data-stu-id="1d41d-114">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="1d41d-115">Ardından, `shadowString` anahtar sözcüğü ile nitelendirilmeden gölgeli sürümü görüntüler `MyBase`  .</span><span class="sxs-lookup"><span data-stu-id="1d41d-115">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="1d41d-116">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1d41d-116">Robust Programming</span></span>

<span data-ttu-id="1d41d-117">Gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini azaltmak için, tüm başvuruları gölgelendirilmiş bir değişkene tamamen niteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d41d-117">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="1d41d-118">Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="1d41d-118">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="1d41d-119">Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1d41d-119">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="1d41d-120">Bu, değişkenin yanlış sürümüne başvurma riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="1d41d-120">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d41d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d41d-121">See also</span></span>

- [<span data-ttu-id="1d41d-122">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="1d41d-122">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="1d41d-123">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="1d41d-123">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="1d41d-124">Gölgeleme ve Geçersiz Kılma Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="1d41d-124">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="1d41d-125">Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme</span><span class="sxs-lookup"><span data-stu-id="1d41d-125">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="1d41d-126">Nasıl yapılır: Devralınmış Değişkeni Gizleme</span><span class="sxs-lookup"><span data-stu-id="1d41d-126">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="1d41d-127">Shadows</span><span class="sxs-lookup"><span data-stu-id="1d41d-127">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="1d41d-128">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="1d41d-128">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="1d41d-129">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="1d41d-129">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="1d41d-130">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="1d41d-130">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
