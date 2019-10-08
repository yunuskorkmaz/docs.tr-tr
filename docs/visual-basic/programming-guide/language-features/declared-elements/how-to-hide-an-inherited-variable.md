---
title: 'Nasıl yapılır: Devralınmış Değişkeni Gizleme (Visual Basic)'
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
ms.openlocfilehash: f575830df44076f694c1dfb2f68379594240fb80
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004851"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="029a3-102">Nasıl yapılır: Devralınmış Değişkeni Gizleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="029a3-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>

<span data-ttu-id="029a3-103">Türetilmiş bir sınıf, temel sınıfının tüm tanımlarını devralır.</span><span class="sxs-lookup"><span data-stu-id="029a3-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="029a3-104">Temel sınıfın bir öğesiyle aynı adı kullanarak bir değişken tanımlamak istiyorsanız, türetilmiş sınıfta değişkeninizi tanımlarken bu temel sınıf öğesini gizleyebilir veya *gölgelendirebilir*.</span><span class="sxs-lookup"><span data-stu-id="029a3-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="029a3-105">Bunu yaparsanız, bu türetilmiş sınıftaki kod, gölgeleme mekanizmasını açıkça atladıkça değişkeninizin erişimine erişir.</span><span class="sxs-lookup"><span data-stu-id="029a3-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>

<span data-ttu-id="029a3-106">Devralınan bir değişkeni gizlemek isteyebileceğiniz diğer bir neden de temel sınıf düzeltmesine karşı koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="029a3-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="029a3-107">Temel sınıf, devraldığınız öğeyi değiştiren bir değişikliği olumsuz etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="029a3-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="029a3-108">Bu durumda, `Shadows` değiştiricisi türetilmiş sınıftan başvuruları, temel sınıf öğesi yerine, değişkeninizden çözümlenecek şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="029a3-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>

## <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="029a3-109">Devralınan bir değişkeni gizlemek için</span><span class="sxs-lookup"><span data-stu-id="029a3-109">To hide an inherited variable</span></span>

1. <span data-ttu-id="029a3-110">Gizlemek istediğiniz değişkenin sınıf düzeyinde (herhangi bir yordam dışında) bildirilmesine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="029a3-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="029a3-111">Aksi takdirde, bunu gizlemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="029a3-111">Otherwise, you do not need to hide it.</span></span>
  
2. <span data-ttu-id="029a3-112">Türetilmiş sınıfınız içinde, değişkeninizi bildiren bir [Dim ekstresi](../../../language-reference/statements/dim-statement.md) yazın.</span><span class="sxs-lookup"><span data-stu-id="029a3-112">Inside your derived class, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="029a3-113">Devralınan değişkenle aynı adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="029a3-113">Use the same name as that of the inherited variable.</span></span>

3. <span data-ttu-id="029a3-114">Bildirime [gölgeler](../../../language-reference/modifiers/shadows.md) anahtar sözcüğünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="029a3-114">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

     <span data-ttu-id="029a3-115">Türetilmiş sınıftaki kod, değişken adına başvurduğunda, derleyici değişkeninizin başvurusunu çözer.</span><span class="sxs-lookup"><span data-stu-id="029a3-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

     <span data-ttu-id="029a3-116">Aşağıdaki örnek, devralınan bir değişkenin gölgelendirdiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="029a3-116">The following example illustrates shadowing of an inherited variable:</span></span>
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="029a3-117">Yukarıdaki örnek, temel sınıfta `shadowString` değişkenini bildirir ve türetilmiş sınıfta gölgeleri.</span><span class="sxs-lookup"><span data-stu-id="029a3-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="029a3-118">Türetilmiş sınıftaki `ShowStrings` yordamı, `shadowString` adı nitelenmediği zaman, dizenin gölgeleme sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="029a3-118">The procedure `ShowStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="029a3-119">Daha sonra, `shadowString` `MyBase` anahtar sözcüğüyle uygun olduğunda gölgeli sürümü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="029a3-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="029a3-120">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="029a3-120">Robust programming</span></span>

<span data-ttu-id="029a3-121">Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="029a3-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="029a3-122">Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="029a3-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="029a3-123">Bu, gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="029a3-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="029a3-124">Gölgelendirilmiş bir değişkene tüm başvuruları tam olarak niteleyerek bu riski düşürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="029a3-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="029a3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="029a3-125">See also</span></span>

- [<span data-ttu-id="029a3-126">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="029a3-126">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="029a3-127">Visual Basic gölgeleme</span><span class="sxs-lookup"><span data-stu-id="029a3-127">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="029a3-128">Gölgeleme ve Geçersiz Kılma Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="029a3-128">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="029a3-129">Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme</span><span class="sxs-lookup"><span data-stu-id="029a3-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="029a3-130">Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme</span><span class="sxs-lookup"><span data-stu-id="029a3-130">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="029a3-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="029a3-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="029a3-132">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="029a3-132">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="029a3-133">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="029a3-133">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
