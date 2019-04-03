---
title: 'Nasıl yapılır: (Visual Basic) türetilmiş sınıf tarafından gizlenen bir değişkene erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: a97a51d4570d87eaa873fb3152ad810f528dff46
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832183"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="2d72d-102">Nasıl yapılır: (Visual Basic) türetilmiş sınıf tarafından gizlenen bir değişkene erişme</span><span class="sxs-lookup"><span data-stu-id="2d72d-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>
<span data-ttu-id="2d72d-103">Kod türetilen bir sınıfta bir değişken eriştiğinde, derleyici en yakın erişilebilir sürüme, yani erişilebilir sürümü başvuru normalde az derivational adımlardan geriye dönük erişen sınıf çözümler.</span><span class="sxs-lookup"><span data-stu-id="2d72d-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="2d72d-104">Değişken türetilmiş sınıf içinde tanımlanmış olması durumunda, kod normalde bu tanımı erişir.</span><span class="sxs-lookup"><span data-stu-id="2d72d-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>  
  
 <span data-ttu-id="2d72d-105">Türetilmiş sınıf değişkeni gölgeleri temel sınıfında bir değişkeni, temel sınıftaki sürümün gizler.</span><span class="sxs-lookup"><span data-stu-id="2d72d-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="2d72d-106">Ancak, kendisiyle uygun temel sınıf değişkenine erişebileceği `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2d72d-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="2d72d-107">Türetilmiş sınıf tarafından gizlenen bir temel sınıf değişkene erişmek için</span><span class="sxs-lookup"><span data-stu-id="2d72d-107">To access a base class variable hidden by a derived class</span></span>  
  
-   <span data-ttu-id="2d72d-108">Bir ifade veya atama ifadesi değişken adıyla önünde `MyBase` anahtar sözcüğü ve bir süre (`.`).</span><span class="sxs-lookup"><span data-stu-id="2d72d-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>  
  
     <span data-ttu-id="2d72d-109">Derleyici, değişkenin temel sınıftaki sürümün başvuruyu çözümler.</span><span class="sxs-lookup"><span data-stu-id="2d72d-109">The compiler resolves the reference to the base class version of the variable.</span></span>  
  
     <span data-ttu-id="2d72d-110">Aşağıdaki örnek, devralma yoluyla gölgeleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d72d-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="2d72d-111">İki başvuru, gölgelendirme değişkeni erişen diğeri, gölgeleme atlar kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2d72d-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="2d72d-112">Yukarıdaki örnekte değişkeni bildirir `shadowString` temel sınıf ve türetilen sınıfta gölgeliyor.</span><span class="sxs-lookup"><span data-stu-id="2d72d-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="2d72d-113">Yordamı `showStrings` türetilmiş bir sınıf içindeki dize gölgeleme sürümünü görüntüler, ad `shadowString` yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="2d72d-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="2d72d-114">Ardından gölgeli sürüm görüntüler, `shadowString` ile tam olduğundan `MyBase` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="2d72d-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2d72d-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2d72d-115">Robust Programming</span></span>  
 <span data-ttu-id="2d72d-116">Gölgeli bir değişkenin istenmeyen bir sürüme başvuran riskini azaltmak için tam olarak gölgeli bir değişken tüm başvuruları kazanabilir.</span><span class="sxs-lookup"><span data-stu-id="2d72d-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="2d72d-117">Gölgeleme, bir değişken aynı ada sahip birden fazla sürümünü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="2d72d-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="2d72d-118">Kod açıklaması değişken adıdır, derleyici başvurusu açığını giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2d72d-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="2d72d-119">Bu değişkeni yanlış sürümüne başvuran riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="2d72d-119">This can increase the risk of referring to the wrong version of the variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d72d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d72d-120">See also</span></span>

- [<span data-ttu-id="2d72d-121">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="2d72d-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="2d72d-122">Visual Basic'de gölgeleme</span><span class="sxs-lookup"><span data-stu-id="2d72d-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="2d72d-123">Gölgeleme ve Geçersiz Kılma Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="2d72d-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="2d72d-124">Nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="2d72d-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="2d72d-125">Nasıl yapılır: Devralınmış değişkeni gizleme</span><span class="sxs-lookup"><span data-stu-id="2d72d-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="2d72d-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="2d72d-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="2d72d-127">Overrides</span><span class="sxs-lookup"><span data-stu-id="2d72d-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="2d72d-128">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="2d72d-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="2d72d-129">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="2d72d-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
