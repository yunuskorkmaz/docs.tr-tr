---
title: Adı &#39; &lt;adı&gt; &#39; bildirilmemiş
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: e52b93980cfc2d162d35b86bd93ce9eeb9875c9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574826"
---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="07dc8-102">Adı &#39; &lt;adı&gt; &#39; bildirilmemiş</span><span class="sxs-lookup"><span data-stu-id="07dc8-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="07dc8-103">Bir deyimi bir programlama öğesine başvuruyor, ancak derleyicinin tam ada sahip bir öğe bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="07dc8-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="07dc8-104">**Hata Kimliği:** BC30451</span><span class="sxs-lookup"><span data-stu-id="07dc8-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="07dc8-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="07dc8-105">To correct this error</span></span>  
  
1. <span data-ttu-id="07dc8-106">Başvuran deyiminde adının yazımını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="07dc8-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="07dc8-107">Visual Basic büyük/küçük harfe duyarsızdır, ancak herhangi bir yazım varyasyonu tamamen farklı bir ad kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="07dc8-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="07dc8-108">Unutmayın, alt çizgi (`_`) adının bir parçası ve bu nedenle yazım parçası.</span><span class="sxs-lookup"><span data-stu-id="07dc8-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2. <span data-ttu-id="07dc8-109">Üye erişimi işleci olup olmadığını denetleyin (`.`) arasında bir nesne ve onun üye.</span><span class="sxs-lookup"><span data-stu-id="07dc8-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="07dc8-110">Örneğin, bir <xref:System.Windows.Forms.TextBox> adlı Denetim `TextBox1`erişmek için kendi <xref:System.Windows.Forms.TextBoxBase.Text%2A> type özelliği `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="07dc8-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="07dc8-111">Bunun yerine, yazarsanız `TextBox1Text`, farklı bir ad oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="07dc8-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3. <span data-ttu-id="07dc8-112">Yazım denetimi doğru olduğundan ve herhangi bir nesne üye erişimi sözdizimini doğru ise, öğesi bildirilmiş doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="07dc8-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="07dc8-113">Daha fazla bilgi için [bildirilen öğeler](../../programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="07dc8-113">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4. <span data-ttu-id="07dc8-114">Programlama öğesine bildirilmişlerse, kapsam içinde olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="07dc8-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="07dc8-115">Başvuran deyimi programlama öğesine bildirme bölge dışında ise, öğe adı nitelemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="07dc8-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="07dc8-116">Daha fazla bilgi için [Visual Basic'de kapsam](../../programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="07dc8-116">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>  

5. <span data-ttu-id="07dc8-117">Tam olarak nitelenmiş tür veya tür ve üye adı kullanmıyorsanız (örneğin, kodunuz bir özellik olarak başvurduğu `MethodInfo.Name` yerine `System.Reflection.MethodInfo.Name`), ekleme bir [Imports deyimi](../statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="07dc8-117">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="07dc8-118">SDK stili projeyi derleyin, çalıştığınız (bir proje ile bir \*satırla başlayan .vbproj dosyası `<Project Sdk="Microsoft.NET.Sdk">`) ve bir tür veya üye Microsoft.VisualBasic.dll içinde hata iletisini ifade eder, uygulamanızı yapılandırın Visual Basic çalışma zamanı kitaplığı için bir başvuru ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="07dc8-118">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="07dc8-119">Varsayılan olarak, SDK stilinde projesinde, bir derlemede kitaplığının bir alt katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="07dc8-119">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="07dc8-120">Örneğin, aşağıdaki örnekte olduğundan derlenemiyor <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> yöntemi bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="07dc8-120">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="07dc8-121">Visual Basic çalışma zamanı, uygulamaya dahil edilen altkümesindeki katıştırılmış değil.</span><span class="sxs-lookup"><span data-stu-id="07dc8-121">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   <span data-ttu-id="07dc8-122">Bu hatayı gidermek için ekleme `<VBRuntime>Default</VBRuntime>` projeleri öğesine `<PropertyGroup>` bölümünde, aşağıdaki gösterildiği gibi Visual Basic proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="07dc8-122">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="07dc8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07dc8-123">See also</span></span>

- [<span data-ttu-id="07dc8-124">Bildirimler ve Sabitlere İlişkin Özet</span><span class="sxs-lookup"><span data-stu-id="07dc8-124">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [<span data-ttu-id="07dc8-125">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="07dc8-125">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="07dc8-126">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="07dc8-126">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="07dc8-127">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="07dc8-127">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
