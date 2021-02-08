---
description: "Hakkında daha fazla bilgi edinin: BC30451: Name ' <name> ' bildirilmemiş"
title: "'<name>' adı bildirilmemiş"
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 8d76bcfd18b277a5f542f363cb906496680bae29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795748"
---
# <a name="bc30451-name-name-is-not-declared"></a><span data-ttu-id="252c8-103">BC30451: Name ' \<name> ' bildirilmemiş</span><span class="sxs-lookup"><span data-stu-id="252c8-103">BC30451: Name '\<name>' is not declared</span></span>

<span data-ttu-id="252c8-104">Bir ifade bir programlama öğesine başvurur, ancak derleyici bu tam adı taşıyan bir öğe bulamaz.</span><span class="sxs-lookup"><span data-stu-id="252c8-104">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>

 <span data-ttu-id="252c8-105">**Hata kimliği:** BC30451</span><span class="sxs-lookup"><span data-stu-id="252c8-105">**Error ID:** BC30451</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="252c8-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="252c8-106">To correct this error</span></span>

1. <span data-ttu-id="252c8-107">Başvuran deyimindeki adın yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="252c8-107">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="252c8-108">Visual Basic, büyük/küçük harfe duyarlıdır, ancak yazıdaki diğer çeşitçler tamamen farklı bir ad olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="252c8-108">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="252c8-109">Alt çizgi ( `_` ) adının bir parçası olduğunu ve bu nedenle Yazımın bir parçasını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="252c8-109">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>

2. <span data-ttu-id="252c8-110">Bir nesne ve üyesi arasında üye erişim işlecine () sahip olup olmadığınızı denetleyin `.` .</span><span class="sxs-lookup"><span data-stu-id="252c8-110">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="252c8-111">Örneğin, <xref:System.Windows.Forms.TextBox> adlı bir denetiminiz varsa `TextBox1` , özelliğine erişmek için <xref:System.Windows.Forms.TextBoxBase.Text%2A> yazmanız gerekir `TextBox1.Text` .</span><span class="sxs-lookup"><span data-stu-id="252c8-111">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="252c8-112">Bunun yerine `TextBox1Text` , farklı bir ad oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="252c8-112">If instead you type `TextBox1Text`, you have created a different name.</span></span>

3. <span data-ttu-id="252c8-113">Yazım doğru ise ve herhangi bir nesne üyesi erişiminin sözdizimi doğru ise, öğenin bildirildiği doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="252c8-113">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="252c8-114">Daha fazla bilgi için bkz. [bildirilmiştir öğeleri](../../programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="252c8-114">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>

4. <span data-ttu-id="252c8-115">Programlama öğesi bildirilirse, kapsam içinde olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="252c8-115">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="252c8-116">Başvuran ifade, programlama öğesini bildiren bölgenin dışındaysa, öğe adını nitelemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="252c8-116">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="252c8-117">Daha fazla bilgi için [Visual Basic kapsam](../../programming-guide/language-features/declared-elements/scope.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="252c8-117">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>

5. <span data-ttu-id="252c8-118">Tam nitelikli bir tür veya tür ve üye adı kullanmıyorsanız (örneğin, kodunuz yerine bir özelliğe başvurur `MethodInfo.Name` `System.Reflection.MethodInfo.Name` ), bir [içeri aktarmalar ekstresi](../statements/imports-statement-net-namespace-and-type.md)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="252c8-118">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="252c8-119">Bir SDK stili proje ( \* satırla başlayan bir. vbproj dosyası olan bir proje) derlemeye çalışıyorsanız `<Project Sdk="Microsoft.NET.Sdk">` ve hata iletisi Microsoft.VisualBasic.dll derlemesinde bir tür veya üyeye başvuruyorsa, uygulamanızı Visual Basic çalışma zamanı kitaplığı başvurusuyla derlemek üzere yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="252c8-119">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="252c8-120">Varsayılan olarak, kitaplığın bir alt kümesi, bir SDK stili projesinde derlemeize katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="252c8-120">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="252c8-121">Örneğin, yöntem bulunamadığı için aşağıdaki örnek derlenemiyor <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="252c8-121">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ChangeType%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="252c8-122">Uygulamanıza dahil olan Visual Basic çalışma zamanının alt kümesine Katıştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="252c8-122">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb?highlight=7)]

   <span data-ttu-id="252c8-123">Bu hatayı gidermek için, `<VBRuntime>Default</VBRuntime>` `<PropertyGroup>` aşağıdaki Visual Basic proje dosyasında gösterildiği gibi, öğesini projeler bölümüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="252c8-123">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-xml[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="252c8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="252c8-124">See also</span></span>

- [<span data-ttu-id="252c8-125">Bildirimler ve Sabitlere İlişkin Özet</span><span class="sxs-lookup"><span data-stu-id="252c8-125">Declarations and Constants Summary</span></span>](../keywords/declarations-and-constants-summary.md)
- [<span data-ttu-id="252c8-126">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="252c8-126">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="252c8-127">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="252c8-127">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="252c8-128">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="252c8-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
