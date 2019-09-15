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
ms.openlocfilehash: dd7ac0487a5878122d9b1717a5e5fc8bf21a4ea7
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972035"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="c71bc-102">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="c71bc-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="c71bc-103">Ad alanları bir derlemede tanımlanan nesneleri düzenler.</span><span class="sxs-lookup"><span data-stu-id="c71bc-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="c71bc-104">Derlemeler birden çok ad alanı içerebilir ve bu da diğer ad alanlarını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="c71bc-105">Ad alanları, sınıf kitaplıkları gibi büyük nesne gruplarını kullanırken belirsizlik ve başvuruları basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="c71bc-106">Örneğin, .NET Framework <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanındaki sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c71bc-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c71bc-107">Aşağıdaki kod parçası, bu sınıf için tam nitelikli adı kullanarak bir değişkenin nasıl bildirilemeyeceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c71bc-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="c71bc-108">Ad çakışmalarını önleme</span><span class="sxs-lookup"><span data-stu-id="c71bc-108">Avoiding Name Collisions</span></span>  
 <span data-ttu-id="c71bc-109">.NET Framework ad alanları, bazen bir sınıf kitaplığı geliştiricisinin başka bir kitaplıktaki benzer adların kullanımıyla birlikte olduğu *ad alanı kirliliğine*de denilen bir sorunu ele alırlar.</span><span class="sxs-lookup"><span data-stu-id="c71bc-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="c71bc-110">Var olan bileşenlerle ilgili bu çakışmalar bazen *ad çarpışmaları*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c71bc-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="c71bc-111">Örneğin, adlı `ListBox`yeni bir sınıf oluşturursanız, bunu proje içinde nitelik olmadan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="c71bc-112">Ancak .NET Framework <xref:System.Windows.Forms.ListBox> sınıfını aynı projede kullanmak istiyorsanız, başvuruyu benzersiz hale getirmek için tam olarak nitelenmiş bir başvuru kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="c71bc-113">Başvuru benzersiz değilse, Visual Basic adın belirsiz olduğunu belirten bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="c71bc-114">Aşağıdaki kod örneği, bu nesnelerin nasıl bildirileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c71bc-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="c71bc-115">Aşağıdaki çizimde adında `ListBox`bir nesne içeren iki ad alanı hiyerarşisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c71bc-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![İki ad alanı hiyerarşisi gösteren ekran görüntüsü.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="c71bc-117">Varsayılan olarak, Visual Basic ile oluşturduğunuz her çalıştırılabilir dosya, projenizle aynı ada sahip bir ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="c71bc-118">Örneğin, adlı `ListBoxProject`bir proje içinde bir nesne tanımlarsanız, ListBoxProject. exe yürütülebilir dosyası adlı `ListBoxProject`bir ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="c71bc-119">Birden çok derleme aynı ad alanını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="c71bc-120">Visual Basic, bunları tek bir ad kümesi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="c71bc-121">Örneğin, adlı `SomeNameSpace` `Assemb1`bir derlemede adlı bir ad alanı için sınıflar tanımlayabilir ve adlı `Assemb2`bir derlemeden aynı ad alanı için ek sınıflar tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="c71bc-122">Tam nitelikli adlar</span><span class="sxs-lookup"><span data-stu-id="c71bc-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="c71bc-123">Tam nitelikli adlar, nesnenin tanımlandığı ad alanının adı önekli nesne başvurulardır.</span><span class="sxs-lookup"><span data-stu-id="c71bc-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="c71bc-124">Sınıfa bir başvuru oluşturursanız ( **Proje** menüsünden **Başvuru Ekle** ' yi seçerek) diğer projelerde tanımlı nesneleri kullanabilirsiniz ve sonra kodunuzda nesne için tam adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c71bc-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="c71bc-125">Aşağıdaki kod parçası, başka bir projenin ad alanından bir nesne için tam olarak nitelenmiş adın nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c71bc-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="c71bc-126">Tam nitelikli adlar, derleyicinin hangi nesnenin kullanılmakta olduğunu belirlemesini olanaklı kıdığından, adlandırma çakışmalarını önler.</span><span class="sxs-lookup"><span data-stu-id="c71bc-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="c71bc-127">Ancak, adları uzun ve çok daha fazla alabilir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="c71bc-128">Bu sorunu gidermek için, bir *diğer*ad tanımlamak `Imports` için ifadesini kullanabilirsiniz — bir tam adı yerine kullanabileceğiniz kısaltılmış bir addır.</span><span class="sxs-lookup"><span data-stu-id="c71bc-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="c71bc-129">Örneğin, aşağıdaki kod örneği iki tam ad için diğer adlar oluşturur ve iki nesneyi tanımlamak için bu diğer adları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c71bc-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="c71bc-130">`Imports` İfadesini bir diğer ad olmadan kullanırsanız, bu ad alanındaki tüm adları, proje için benzersiz olmaları şartıyla, nitelendirme olmadan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="c71bc-131">Projeniz aynı ada sahip `Imports` öğeleri içeren ad alanları için deyimler içeriyorsa, bu adı kullandığınızda bu adı tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="c71bc-132">Örneğin, projenizin aşağıdaki iki `Imports` deyimi içerdiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="c71bc-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="c71bc-133">Tam nitelikli olmadan kullanmaya `Class1` çalışırsanız, Visual Basic adın `Class1` belirsiz olduğunu belirten bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="c71bc-134">Ad alanı düzeyi deyimleri</span><span class="sxs-lookup"><span data-stu-id="c71bc-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="c71bc-135">Bir ad alanı içinde modüller, arabirimler, sınıflar, temsilciler, numaralandırmalar, yapılar ve diğer ad alanları gibi öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="c71bc-136">Ad alanı düzeyinde özellikler, yordamlar, değişkenler ve olaylar gibi öğeleri tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="c71bc-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="c71bc-137">Bu öğeler modüller, yapılar veya sınıflar gibi kapsayıcılar içinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="c71bc-138">Tam adlarda genel anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="c71bc-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="c71bc-139">İç içe geçmiş bir ad alanı hiyerarşisi tanımladıysanız, bu hiyerarşinin içindeki kodun .NET Framework <xref:System?displayProperty=nameWithType> ad alanına erişmesi engellenebilir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="c71bc-140">Aşağıdaki örnekte, `SpecialSpace.System` ad alanının <xref:System?displayProperty=nameWithType>erişimini engellediği bir hiyerarşi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="c71bc-141">Sonuç olarak, Visual Basic derleyici öğesine <xref:System.Int32?displayProperty=nameWithType>başvurusunu başarıyla çözümleyemiyor, çünkü `SpecialSpace.System` tanımlamaz `Int32`.</span><span class="sxs-lookup"><span data-stu-id="c71bc-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="c71bc-142">`Global` Anahtar sözcüğünü, .NET Framework sınıf kitaplığının en dıştaki düzeyinde nitelik zinciri başlatmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="c71bc-143">Bu, <xref:System?displayProperty=nameWithType> sınıf kitaplığında ad alanı veya diğer ad alanı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c71bc-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="c71bc-144">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="c71bc-145">Gibi diğer kök `Global` düzeyi ad alanlarına <xref:Microsoft.VisualBasic?displayProperty=nameWithType>ve projenizle ilişkili herhangi bir ad alanına erişmek için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="c71bc-146">Namespace deyimlerde Global anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c71bc-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="c71bc-147">Bir `Global` [Namespace deyimindeki](../../../visual-basic/language-reference/statements/namespace-statement.md)anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="c71bc-148">Bu, projenizin kök ad alanından bir ad alanı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c71bc-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="c71bc-149">Projenizdeki tüm ad alanları, projenin kök ad alanını temel alır.</span><span class="sxs-lookup"><span data-stu-id="c71bc-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="c71bc-150">Visual Studio, projenizdeki tüm kodlar için proje adınızı varsayılan kök ad alanı olarak atar.</span><span class="sxs-lookup"><span data-stu-id="c71bc-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="c71bc-151">Örneğin, projeniz adlandırılmışsa `ConsoleApplication1`, programlama öğeleri ad alanına `ConsoleApplication1`aittir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="c71bc-152">Bildirirseniz `Namespace Magnetosphere`, projedeki `Magnetosphere` başvuruları erişir `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="c71bc-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="c71bc-153">Aşağıdaki örneklerde, projenin kök `Global` ad alanından dışarı bir ad alanı bildirmek için anahtar sözcüğü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c71bc-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="c71bc-154">Bir ad alanı bildiriminde, `Global` başka bir ad alanında iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="c71bc-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="c71bc-155">Projenin **kök ad alanını** görüntülemek ve değiştirmek Için [uygulama sayfasını, Proje tasarımcısı 'nı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="c71bc-156">Yeni projeler için, **kök ad alanı** varsayılan olarak proje adı olur.</span><span class="sxs-lookup"><span data-stu-id="c71bc-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="c71bc-157">En üst düzey ad alanı olmasını sağlamak için, **kök ad alanı** girişini temizleyerek kutunun boş olması gerekir. `Global`</span><span class="sxs-lookup"><span data-stu-id="c71bc-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="c71bc-158">**Kök ad alanını** Temizleme, ad alanı bildirimlerinde `Global` anahtar kelimesinin gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c71bc-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="c71bc-159">Bir `Namespace` deyimde .NET Framework bir ad alanı olan bir ad bildirirse, `Global` anahtar sözcüğü tam bir ad içinde kullanılmıyorsa, .NET Framework ad alanı kullanılamaz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="c71bc-160">`Global` Anahtar sözcüğünü kullanmadan bu .NET Framework ad alanına erişimi etkinleştirmek için, `Global` anahtar sözcüğünü `Namespace` deyime ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="c71bc-161">Aşağıdaki örnek `Global` , `System.Text` ad alanı bildiriminde anahtar kelimedir.</span><span class="sxs-lookup"><span data-stu-id="c71bc-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="c71bc-162">Anahtar sözcüğü ad alanı bildiriminde yoksa, <xref:System.Text.StringBuilder> belirtilmeden `Global.System.Text.StringBuilder`erişilemez. `Global`</span><span class="sxs-lookup"><span data-stu-id="c71bc-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="c71bc-163">Adlı `ConsoleApplication1`bir proje için, `Global` anahtar sözcüğü `System.Text` kullanılsaydı `ConsoleApplication1.System.Text` başvurular erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c71bc-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="c71bc-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c71bc-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="c71bc-165">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="c71bc-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="c71bc-166">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="c71bc-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="c71bc-167">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="c71bc-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c71bc-168">Office Çözümlerinde Kod Yazma</span><span class="sxs-lookup"><span data-stu-id="c71bc-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
