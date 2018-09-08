---
title: Visual Basic'de Ad Alanları
ms.date: 07/20/2015
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
ms.openlocfilehash: 6b320d21c33fa798ca2fd3ef5a04363d141f99f2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44202199"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="eb1c0-102">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="eb1c0-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="eb1c0-103">Ad alanları, bir derlemede tanımlanan nesneler düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="eb1c0-104">Derlemeleri diğer ad alanlarında sırayla içerebilen birden çok ad alanları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="eb1c0-105">Ad alanları belirsizlik önlemek ve büyük nesne grupları gibi sınıf kitaplıkları kullanırken başvuruları basitleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="eb1c0-106">Örneğin, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tanımlar <xref:System.Windows.Forms.ListBox> sınıfını <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-106">For example, the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="eb1c0-107">Aşağıdaki kod parçası, bu sınıfın tam adını kullanarak bir değişken bildirmek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="eb1c0-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="eb1c0-108">Ad çakışmalarını önleme</span><span class="sxs-lookup"><span data-stu-id="eb1c0-108">Avoiding Name Collisions</span></span>  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]<span data-ttu-id="eb1c0-109"> ad alanları olarak da adlandırılan bir sorun gidermek \*ad alanı kirliliği\*, başka bir kitaplık benzer adlarında kullanımı, bir sınıf kitaplığı geliştiricisi belgelemenin içinde.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-109"> namespaces address a problem sometimes called \*namespace pollution\*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="eb1c0-110">Bu çakışmaları var olan bileşenleri ile adlandırılan *adı Çarpışmaları*.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="eb1c0-111">Örneğin, adında yeni bir sınıf oluşturursanız `ListBox`, nitelik olmadan proje içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="eb1c0-112">Ancak, kullanmak istiyorsanız [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> sınıfı aynı projede benzersiz başvuru yapmak için tam nitelikli bir başvuru kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-112">However, if you want to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="eb1c0-113">Başvuru benzersiz değilse, Visual Basic adı belirsiz bildiren bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="eb1c0-114">Aşağıdaki kod örneği, bu nesneleri bildirmek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="eb1c0-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 <span data-ttu-id="eb1c0-115">Her iki içeren adlı bir nesne iki ad alanı hiyerarşileri, aşağıdaki çizimde `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`.</span></span>  
  
 <span data-ttu-id="eb1c0-116">![Namespace hiyerarşi](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span><span class="sxs-lookup"><span data-stu-id="eb1c0-116">![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span></span>  
  
 <span data-ttu-id="eb1c0-117">Varsayılan olarak, Visual Basic ile oluşturduğunuz her bir yürütülebilir dosya projeniz gibi aynı ada sahip bir ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="eb1c0-118">Örneğin, bir nesne adlı bir proje içinde tanımlarsanız `ListBoxProject`, yürütülebilir dosyayı ListBoxProject.exe adlı bir ad alanı içeren `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="eb1c0-119">Birden çok derleme, aynı ad alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="eb1c0-120">Visual Basic, bunları tek bir ad kümesini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="eb1c0-121">Örneğin, sınıflar adlandırılan bir ad alanı için tanımlayabileceğiniz `SomeNameSpace` adlı bir derlemede `Assemb1`ve aynı ad alanından adlı bir derleme için ek sınıfları tanımlama `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="eb1c0-122">Tam olarak nitelenmiş adlar</span><span class="sxs-lookup"><span data-stu-id="eb1c0-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="eb1c0-123">Tam nesne tanımlandığı ad alanı adı ile ön ekli nesne başvuruları adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="eb1c0-124">Sınıfa bir başvuru oluşturursanız, diğer projelerde tanımlanan nesneler kullanabilirsiniz (seçerek **Başvuru Ekle** gelen **proje** menüsü) ve kodunuzda nesnenin tam adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="eb1c0-125">Aşağıdaki kod parçası, başka bir projenin ad alanındaki nesnenin tam adı kullanma işlemini gösterir:</span><span class="sxs-lookup"><span data-stu-id="eb1c0-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 <span data-ttu-id="eb1c0-126">Tam olarak nitelenmiş adlar önlemek adlandırma bunlar derleyicinin nesnenin kullanıldığını belirlemek mümkün kılar çünkü çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="eb1c0-127">Ancak, adları, uzun ve çetrefilli elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="eb1c0-128">Bu sorunu aşmak için kullanabileceğiniz `Imports` deyimi tanımlamak için bir *diğer*— kısaltılmış adı yerine tam adını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="eb1c0-129">Örneğin, aşağıdaki kod örneği, iki tam olarak nitelenmiş adlar için diğer ad oluşturur ve bu diğer adlar iki nesneleri tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 <span data-ttu-id="eb1c0-130">Kullanırsanız `Imports` deyimi bir diğer ad, projeye benzersiz oldukları içeren ad niteliği olmadan sağlanan tüm adlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="eb1c0-131">Projeniz içeriyorsa `Imports` deyimleri aynı ada sahip öğeleri içeren ad alanları için tam olarak nitelemeniz gerekir adı kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="eb1c0-132">Örneğin, projeniz aşağıdaki iki içeriyordu. varsayalım `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="eb1c0-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 <span data-ttu-id="eb1c0-133">Kullanmayı denerseniz `Class1` tam olarak niteleme olmadan, Visual Basic belirten bir hatayla adı üretir `Class1` belirsiz.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="eb1c0-134">Namespace düzeyi deyimleri</span><span class="sxs-lookup"><span data-stu-id="eb1c0-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="eb1c0-135">Ad alanı içinde modüller, arabirimler, sınıflar, temsilciler, numaralandırmalar, yapılar ve diğer ad alanları gibi öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="eb1c0-136">Özellikler, yordamlar, değişkenler ve ad alanı düzeyinde olaylar gibi öğeleri tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="eb1c0-137">Bu öğeleri modülleri, yapılar ve sınıflar gibi kapsayıcıları içinde bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="eb1c0-138">Global anahtar sözcüğü, tam olarak nitelenmiş adlar</span><span class="sxs-lookup"><span data-stu-id="eb1c0-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="eb1c0-139">İç içe geçmiş ad alanları hiyerarşisi tanımladıysanız, söz konusu hiyerarşi içinde kod erişimi engellenebilir <xref:System?displayProperty=nameWithType> ad alanı .NET Framework'ün.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="eb1c0-140">Bir hiyerarşide aşağıdaki örnekte `SpecialSpace.System` ad alanı blokları erişim <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="eb1c0-141">Sonuç olarak, Visual Basic Derleyicisi başvuru başarıyla çözümlenemiyor <xref:System.Int32?displayProperty=nameWithType>, çünkü `SpecialSpace.System` tanımlamaz `Int32`.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="eb1c0-142">Kullanabileceğiniz `Global` .NET Framework sınıf kitaplığı, en dıştaki düzeyinde nitelik zinciri başlatmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="eb1c0-143">Bu sayede belirtmek <xref:System?displayProperty=nameWithType> ad alanı veya Sınıf Kitaplığı'nda herhangi bir ad.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="eb1c0-144">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-144">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="eb1c0-145">Kullanabileceğiniz `Global` erişim gibi diğer kök düzeyinde ad alanları için <xref:Microsoft.VisualBasic?displayProperty=nameWithType>ve projenizle ilişkili herhangi bir ad alanı.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="eb1c0-146">Global anahtar sözcüğü Namespace deyimlerinde</span><span class="sxs-lookup"><span data-stu-id="eb1c0-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="eb1c0-147">Ayrıca `Global` anahtar sözcüğü bir [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="eb1c0-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="eb1c0-148">Bu, bir ad alanı, projenin kök ad dışında tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="eb1c0-149">Projenizdeki tüm ad alanlarını projenin kök ad alanını temel alır.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="eb1c0-150">Visual Studio proje adınız, projenizdeki tüm kodlar için varsayılan kök ad alanı olarak atar.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="eb1c0-151">Örneğin, projeniz `ConsoleApplication1`, ad alanına programlama öğelerine ait `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="eb1c0-152">Bildirirseniz `Namespace Magnetosphere`, başvurular `Magnetosphere` projede erişecek `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="eb1c0-153">Aşağıdaki örneklerde `Global` projenin kök ad alanı dışında bir ad alanı bildirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 <span data-ttu-id="eb1c0-154">Bir ad alanı bildiriminde `Global` başka bir ad alanında iç içe olamaz.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="eb1c0-155">Kullanabileceğiniz [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) görüntülemek ve değiştirmek için **kök Namespace** proje.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="eb1c0-156">Yeni projelerde **kök Namespace** varsayılan olarak projenin adı.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="eb1c0-157">Neden `Global` en üst düzey ad olacak şekilde temizleyebilir **kök Namespace** giriş kutusu boş olmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="eb1c0-158">Temizleme **kök Namespace** gereksinimini ortadan kaldırır `Global` anahtar sözcük ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="eb1c0-159">Varsa bir `Namespace` ifade, bir ad alanı .NET Framework ayrıca bir ad bildirir, .NET Framework ad alanı kullanılamaz hale gelmesi durumunda `Global` anahtar sözcüğü, bir tam adı kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="eb1c0-160">Kullanmadan, .NET Framework ad alanına erişimi etkinleştirmek için `Global` anahtar sözcüğünü içerebilir `Global` anahtar sözcüğünü `Namespace` deyimi.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="eb1c0-161">Aşağıdaki örnek sahip `Global` anahtar sözcüğünü `System.Text` ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="eb1c0-162">Varsa `Global` anahtar sözcüğü ad alanı bildiriminde mevcut değildi <xref:System.Text.StringBuilder> belirtmeden erişilemedi `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="eb1c0-163">Adlı bir proje için `ConsoleApplication1`, başvurular `System.Text` eriştiğiniz `ConsoleApplication1.System.Text` varsa `Global` anahtar sözcüğü değil kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="eb1c0-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>  
- <xref:System.Windows.Forms?displayProperty=nameWithType>  
- [<span data-ttu-id="eb1c0-165">Derlemeler ve Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="eb1c0-165">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="eb1c0-166">Nasıl yapılır: Komut Satırını Kullanarak Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="eb1c0-166">How to: Create and Use Assemblies Using the Command Line</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)  
- [<span data-ttu-id="eb1c0-167">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="eb1c0-167">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
- [<span data-ttu-id="eb1c0-168">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="eb1c0-168">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
- [<span data-ttu-id="eb1c0-169">Office Çözümlerinde Kod Yazma</span><span class="sxs-lookup"><span data-stu-id="eb1c0-169">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
