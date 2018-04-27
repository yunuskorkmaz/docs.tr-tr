---
title: Visual Basic'de Ad Alanları
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ec038a17b4a6b10dbe339fe33969c4ade57e2a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="31217-102">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="31217-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="31217-103">Ad alanları, bir derlemede tanımlanan nesneleri düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="31217-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="31217-104">Derlemeleri sırayla diğer ad içeren birden çok ad alanları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="31217-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="31217-105">Ad alanları, Karışıklığı önlemek ve nesneleri oluşan büyük gruplar gibi sınıf kitaplıkları kullanırken başvuruları basitleştirin.</span><span class="sxs-lookup"><span data-stu-id="31217-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="31217-106">Örneğin, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tanımlar <xref:System.Windows.Forms.ListBox> sınıfını <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="31217-106">For example, the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="31217-107">Aşağıdaki kod parçası, bu sınıf için tam olarak nitelenmiş adını kullanarak bir değişken bildirme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="31217-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="31217-108">Ad çakışmaları önleme</span><span class="sxs-lookup"><span data-stu-id="31217-108">Avoiding Name Collisions</span></span>  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]<span data-ttu-id="31217-109"> ad alanları olarak da adlandırılan bir sorun adres *ad alanı kirliliği*, başka bir kitaplıktaki benzer adlarının kullanımını da bir sınıf kitaplığı Geliştirici hampered içinde.</span><span class="sxs-lookup"><span data-stu-id="31217-109"> namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="31217-110">Var olan bileşenleri ile bu çakışmaları adlandırılan *ad çakışması*.</span><span class="sxs-lookup"><span data-stu-id="31217-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="31217-111">Adlı yeni bir sınıf oluşturursanız, örneğin, `ListBox`, projenizin niteliğe olmadan içinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="31217-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="31217-112">Ancak, kullanmak istiyorsanız, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> sınıfı aynı projede başvuru benzersiz hale getirmek için tam bir başvuru kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="31217-112">However, if you want to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="31217-113">Visual Basic başvurusu benzersiz değilse, adı belirsiz olduğunu bildiren bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="31217-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="31217-114">Aşağıdaki kod örneği, bu nesnelerin bildirme gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="31217-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 <span data-ttu-id="31217-115">Her iki içeren adlı bir nesne iki ad alanı hiyerarşileri aşağıda gösterilmiştir `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="31217-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`.</span></span>  
  
 <span data-ttu-id="31217-116">![Namespace hiyerarşi](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span><span class="sxs-lookup"><span data-stu-id="31217-116">![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span></span>  
  
 <span data-ttu-id="31217-117">Varsayılan olarak, Visual Basic ile oluşturduğunuz her yürütülebilir dosyayı projenize aynı ada sahip bir ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="31217-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="31217-118">Örneğin, bir nesne adlı bir projede tanımlarsanız `ListBoxProject`, yürütülebilir dosya ListBoxProject.exe adlı bir ad alanı içeren `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="31217-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="31217-119">Birden çok derleme aynı ad alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31217-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="31217-120">Visual Basic bunları adları tek bir dizi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="31217-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="31217-121">Örneğin, sınıfları adlı bir ad alanı için tanımlayabilirsiniz `SomeNameSpace` adlı bir bütünleştirilmiş `Assemb1`ve aynı ad alanından adlı bir derleme için ek sınıflarını tanımla `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="31217-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="31217-122">Tam olarak nitelenmiş adlar</span><span class="sxs-lookup"><span data-stu-id="31217-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="31217-123">Nesne tanımlandığı ad alanı adı ile önek nesne başvuruları tam adlardır.</span><span class="sxs-lookup"><span data-stu-id="31217-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="31217-124">Sınıfının bir başvurusunu oluşturursanız, diğer projelerinde tanımlanmış nesneleri kullanabilirsiniz (seçerek **Başvuru Ekle** gelen **proje** menüsü) ve sonra kodunuzda nesne için tam ad kullanın.</span><span class="sxs-lookup"><span data-stu-id="31217-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="31217-125">Aşağıdaki kod parçası, başka bir projenin ad alanından bir nesne için tam ad kullanmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="31217-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 <span data-ttu-id="31217-126">Tam olarak nitelenmiş adlar önlemek adlandırma bunlar derleyici hangi nesne kullanıldığını belirlemek olası hale çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="31217-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="31217-127">Ancak, adları kendilerini uzun ve sıkıcı elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31217-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="31217-128">Bu sorunu almak için kullanabileceğiniz `Imports` tanımlamak için deyimi bir *diğer*— bir tam ad yerine kullanabileceğiniz bir kısaltılmış adı.</span><span class="sxs-lookup"><span data-stu-id="31217-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="31217-129">Örneğin, aşağıdaki kod örneği iki tam olarak nitelenmiş adlar için diğer adlar oluşturur ve bu diğer adlar iki nesneleri tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31217-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 <span data-ttu-id="31217-130">Kullanırsanız `Imports` deyimi bir diğer ad olmadan nitelik, ad alanının sağlandığından, projeye benzersiz oldukları tüm adlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31217-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="31217-131">Projeniz içeriyorsa `Imports` deyimleri aynı ada sahip öğe içeren ad alanları için gereken tam olarak nitelemek bu adı kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="31217-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="31217-132">Örneğin, aşağıdaki iki projeniz bulunan varsayalım `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="31217-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 <span data-ttu-id="31217-133">Kullanmayı denerseniz, `Class1` tam niteleme olmadan, Visual Basic, bildiren bir hata adı üretir `Class1` belirsiz.</span><span class="sxs-lookup"><span data-stu-id="31217-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="31217-134">Namespace düzeyi deyimleri</span><span class="sxs-lookup"><span data-stu-id="31217-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="31217-135">Ad alanı içinde modüller, arabirimleri, sınıflar, temsilciler, numaralandırmalar, yapılar ve diğer ad alanları gibi öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31217-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="31217-136">Özellikler, yordamlar, değişkenler ve ad alanı düzeyinde olayları gibi öğeleri tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="31217-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="31217-137">Bu öğeler, modüller, yapıları ve sınıfları gibi kapsayıcılarına içinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="31217-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="31217-138">Tam olarak nitelenmiş adlar genel anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="31217-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="31217-139">Ad alanları iç içe geçmiş hiyerarşisini tanımladıysanız, bu hiyerarşi içinde kod erişmesi engellenebilir <xref:System?displayProperty=nameWithType> ad alanı .NET Framework'ün.</span><span class="sxs-lookup"><span data-stu-id="31217-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="31217-140">Aşağıdaki örnek bir hiyerarşide gösterilmektedir `SpecialSpace.System` ad alanı erişimi için <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31217-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="31217-141">Sonuç olarak, Visual Basic derleyici başarıyla başvurusu çözümlenemiyor <xref:System.Int32?displayProperty=nameWithType>, çünkü `SpecialSpace.System` tanımlamaz `Int32`.</span><span class="sxs-lookup"><span data-stu-id="31217-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="31217-142">Kullanabileceğiniz `Global` .NET Framework sınıf kitaplığı en dıştaki düzeyinde niteliğe zinciri başlatmak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="31217-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="31217-143">Bu sayede belirtmek <xref:System?displayProperty=nameWithType> ad alanı veya diğer ad alanı Sınıf Kitaplığı'nda.</span><span class="sxs-lookup"><span data-stu-id="31217-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="31217-144">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="31217-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="31217-145">Kullanabileceğiniz `Global` erişim gibi diğer kök düzeyinde ad alanları için <xref:Microsoft.VisualBasic?displayProperty=nameWithType>ve projenizi ile ilişkili herhangi bir ad alanı.</span><span class="sxs-lookup"><span data-stu-id="31217-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="31217-146">Namespace deyimlerinde genel anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="31217-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="31217-147">Aynı zamanda `Global` in anahtar sözcüğü bir [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="31217-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="31217-148">Bu, bir ad alanı, projenin kök ad alanı dışında tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="31217-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="31217-149">Tüm ad alanlarını projenizdeki projesinin kök ad alanı esas alır.</span><span class="sxs-lookup"><span data-stu-id="31217-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="31217-150">Visual Studio Proje adına projenizdeki tüm kodları için varsayılan kök ad alanı olarak atar.</span><span class="sxs-lookup"><span data-stu-id="31217-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="31217-151">Örneğin, projenizin adlı `ConsoleApplication1`, programlama öğeleri ad alanına ait `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="31217-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="31217-152">Bildirirseniz `Namespace Magnetosphere`, başvurular `Magnetosphere` projede erişecek `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="31217-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="31217-153">Aşağıdaki örneklerde `Global` projesinin kök ad alanı dışında bir ad alanı bildirmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="31217-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 <span data-ttu-id="31217-154">Bir ad alanı bildirimi `Global` başka bir ad alanında iç içe olamaz.</span><span class="sxs-lookup"><span data-stu-id="31217-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="31217-155">Kullanabileceğiniz [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) görüntülemek ve değiştirmek için **kök Namespace** projenin.</span><span class="sxs-lookup"><span data-stu-id="31217-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="31217-156">Yeni projeler için **kök Namespace** proje adının varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="31217-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="31217-157">Neden `Global` en üst düzey ad olacak şekilde, temizleyebilirsiniz **kök Namespace** giriş kutusu boş olmasını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="31217-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="31217-158">Temizleme **kök Namespace** gereksinimini ortadan kaldırır `Global` ad alanı bildirimleri anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="31217-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="31217-159">Varsa bir `Namespace` ifade, bir ad alanı .NET Framework ayrıca bir ad bildirir, .NET Framework ad kullanılamaz hale varsa `Global` anahtar sözcüğü bir tam ad kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="31217-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="31217-160">Kullanmadan, .NET Framework ad alanına erişimi etkinleştirmek için `Global` anahtar sözcüğü, içerebilir `Global` anahtar sözcük `Namespace` deyimi.</span><span class="sxs-lookup"><span data-stu-id="31217-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="31217-161">Aşağıdaki örnek sahip `Global` anahtar sözcük `System.Text` ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="31217-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="31217-162">Varsa `Global` anahtar sözcük ad alanı bildirimi mevcut değildi <xref:System.Text.StringBuilder> belirtmeden erişilemedi `Global.System.Text.StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="31217-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="31217-163">Adlı bir proje için `ConsoleApplication1`, başvurular `System.Text` erişir `ConsoleApplication1.System.Text` varsa `Global` anahtar sözcüğü olmayan kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="31217-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="31217-164">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31217-164">See Also</span></span>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
 [<span data-ttu-id="31217-165">Derlemeler ve Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="31217-165">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="31217-166">Nasıl yapılır: Komut Satırını Kullanarak Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="31217-166">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="31217-167">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="31217-167">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="31217-168">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="31217-168">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="31217-169">Office Çözümlerinde Kod Yazma</span><span class="sxs-lookup"><span data-stu-id="31217-169">Writing Code in Office Solutions</span></span>](https://msdn.microsoft.com/library/bb608596)
