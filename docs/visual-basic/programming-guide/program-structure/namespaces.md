---
title: Ad Alanları
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
ms.openlocfilehash: ec892167f30a7ded739dc188ab4096cb3a5d154c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400675"
---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="fbab5-102">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="fbab5-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="fbab5-103">Ad alanları bir derlemede tanımlanan nesneleri düzenler.</span><span class="sxs-lookup"><span data-stu-id="fbab5-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="fbab5-104">Derlemeler, sırayla diğer ad alanları içerebilir birden çok ad alanı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="fbab5-105">Ad alanları, sınıf kitaplıkları gibi büyük nesne grupları kullanırken belirsizliği önler ve başvuruları basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="fbab5-106">Örneğin, .NET Framework <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanındaki sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fbab5-106">For example, the .NET Framework defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="fbab5-107">Aşağıdaki kod parçası, bu sınıf için tam nitelikli adı kullanarak bir değişkenin nasıl bildirilir:</span><span class="sxs-lookup"><span data-stu-id="fbab5-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="fbab5-108">Ad Çarpışmalarından Kaçınma</span><span class="sxs-lookup"><span data-stu-id="fbab5-108">Avoiding Name Collisions</span></span>  
 <span data-ttu-id="fbab5-109">.NET Framework ad alanları, sınıf kitaplığı geliştiricisinin başka bir kitaplıkta benzer adların kullanılmasıyla engellendiği bazen *ad alanı kirliliği*olarak adlandırılan bir sorunu giderır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-109">.NET Framework namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="fbab5-110">Varolan bileşenlerle bu çakışmalar bazen *ad çakışmaları*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-110">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="fbab5-111">Örneğin, adlı `ListBox`yeni bir sınıf oluşturursanız, bu sınıfı projenizde niteliksiz kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-111">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="fbab5-112">Ancak, .NET Framework <xref:System.Windows.Forms.ListBox> sınıfını aynı projede kullanmak istiyorsanız, başvuruyu benzersiz kılmak için tam nitelikli bir başvuru kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-112">However, if you want to use the .NET Framework <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="fbab5-113">Başvuru benzersiz değilse, Visual Basic adı belirsiz olduğunu belirten bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-113">If the reference is not unique, Visual Basic produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="fbab5-114">Aşağıdaki kod örneği, bu nesnelerin nasıl bildirilen gösteriş gösterir:</span><span class="sxs-lookup"><span data-stu-id="fbab5-114">The following code example demonstrates how to declare these objects:</span></span>  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 <span data-ttu-id="fbab5-115">Aşağıdaki resimde, her ikisi de adlandırılmış `ListBox`bir nesne içeren iki ad alanı hiyerarşisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="fbab5-115">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`:</span></span>  
  
 ![İki ad alanı hiyerarşisi gösteren ekran görüntüsü.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 <span data-ttu-id="fbab5-117">Varsayılan olarak, Visual Basic ile oluşturduğunuz her yürütülebilir dosya, projenizle aynı ada sahip bir ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-117">By default, every executable file you create with Visual Basic contains a namespace with the same name as your project.</span></span> <span data-ttu-id="fbab5-118">Örneğin, adlı `ListBoxProject`bir proje içinde bir nesne tanımlarsanız, yürütülebilir dosya ListBoxProject.exe adlı `ListBoxProject`bir ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-118">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="fbab5-119">Birden çok derleme aynı ad alanını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-119">Multiple assemblies can use the same namespace.</span></span> <span data-ttu-id="fbab5-120">Visual Basic bunları tek bir ad kümesi olarak ele adatır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-120">Visual Basic treats them as a single set of names.</span></span> <span data-ttu-id="fbab5-121">Örneğin, adlı `SomeNameSpace` `Assemb1`bir derlemede adı geçen bir ad alanı için sınıfları tanımlayabilir ve `Assemb2`aynı ad alanı için ek sınıflar tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-121">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="fbab5-122">Tam Nitelikli İsimler</span><span class="sxs-lookup"><span data-stu-id="fbab5-122">Fully Qualified Names</span></span>  
 <span data-ttu-id="fbab5-123">Tam nitelikli adlar, nesnenin tanımlandığı ad alanının adı ile önceden belirlenmiş nesne başvurularıdır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-123">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="fbab5-124">Sınıfa bir başvuru oluşturursanız **(Proje** menüsünden **Referans Ekle'yi** seçerek) ve ardından kodunuzdaki nesne için tam nitelikli adı kullanırsanız, diğer projelerde tanımlanan nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-124">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="fbab5-125">Aşağıdaki kod parçası, başka bir projenin ad alanından bir nesne için tam nitelikli adın nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="fbab5-125">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 <span data-ttu-id="fbab5-126">Tam nitelikli adlar, derleyicinin hangi nesnenin kullanıldığını belirlemesini mümkün kıldığı için çakışmaları engeller.</span><span class="sxs-lookup"><span data-stu-id="fbab5-126">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="fbab5-127">Ancak, isimleri kendilerini uzun ve hantal alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-127">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="fbab5-128">Bunu aşmak `Imports` için, tam nitelikli bir ad yerine kullanabileceğiniz kısaltılmış bir ad olan bir takma *ad*tanımlamak için deyimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-128">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="fbab5-129">Örneğin, aşağıdaki kod örneği iki tam nitelikli ad için takma adlar oluşturur ve bu diğer adları iki nesne tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-129">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 <span data-ttu-id="fbab5-130">İfadeyi `Imports` takma ad olmadan kullanırsanız, projeye özgü olmaları koşuluyla, bu ad alanındaki tüm adları nitelik siz de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-130">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="fbab5-131">Projeniz aynı `Imports` ada sahip öğeler içeren ad alanları için deyimler içeriyorsa, bu adı kullandığınızda tam olarak nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-131">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="fbab5-132">Örneğin, projenizin aşağıdaki iki `Imports` deyim içerdiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="fbab5-132">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 <span data-ttu-id="fbab5-133">Tam olarak nitelemeden kullanmaya `Class1` çalışırsanız, Visual Basic adının `Class1` belirsiz olduğunu belirten bir hata üretir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-133">If you attempt to use `Class1` without fully qualifying it, Visual Basic produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="fbab5-134">Ad Alanı Düzey İfadeleri</span><span class="sxs-lookup"><span data-stu-id="fbab5-134">Namespace Level Statements</span></span>  
 <span data-ttu-id="fbab5-135">Ad alanı içinde, modüller, arabirimler, sınıflar, temsilciler, sayısallamalar, yapılar ve diğer ad alanları gibi öğeleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-135">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="fbab5-136">Ad alanı düzeyinde özellikler, yordamlar, değişkenler ve olaylar gibi öğeleri tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fbab5-136">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="fbab5-137">Bu öğeler modüller, yapılar veya sınıflar gibi kapsayıcılar içinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-137">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="fbab5-138">Tam Nitelikli Adlarda Genel Anahtar Kelime</span><span class="sxs-lookup"><span data-stu-id="fbab5-138">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="fbab5-139">Ad alanları iç içe bir hiyerarşi tanımladıysanız, bu hiyerarşiiçindeki kodun .NET <xref:System?displayProperty=nameWithType> Framework ad alanına erişmeleri engellenebilir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-139">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=nameWithType> namespace of the .NET Framework.</span></span> <span data-ttu-id="fbab5-140">Aşağıdaki örnekte, ad alanının `SpecialSpace.System` . <xref:System?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fbab5-140">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=nameWithType>.</span></span>  
  
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
  
 <span data-ttu-id="fbab5-141">Sonuç olarak, Visual Basic derleyicisi başvuruyu <xref:System.Int32?displayProperty=nameWithType>başarıyla çözemiyor , çünkü `SpecialSpace.System` tanımlamaz. `Int32`</span><span class="sxs-lookup"><span data-stu-id="fbab5-141">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=nameWithType>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="fbab5-142">.NET Framework `Global` sınıf kitaplığı en dış düzeyinde yeterlilik zincirini başlatmak için anahtar kelimeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-142">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="fbab5-143">Bu, sınıf kitaplığındaki <xref:System?displayProperty=nameWithType> ad alanını veya başka bir ad alanını belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbab5-143">This allows you to specify the <xref:System?displayProperty=nameWithType> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="fbab5-144">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-144">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="fbab5-145">Diğer kök `Global` düzeyindeki <xref:Microsoft.VisualBasic?displayProperty=nameWithType>ad alanlarına ve projenizle ilişkili ad alanına erişmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-145">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="fbab5-146">Ad Alanı İfadelerinde Genel Anahtar Kelime</span><span class="sxs-lookup"><span data-stu-id="fbab5-146">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="fbab5-147">`Global` Anahtar sözcüğü Ad Alanı [Bildirimi'nde](../../../visual-basic/language-reference/statements/namespace-statement.md)de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-147">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="fbab5-148">Bu, projenizin kök ad alanından bir ad alanı tanımlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-148">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="fbab5-149">Projenizdeki tüm ad alanları, projenin kök ad alanını temel adatır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-149">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="fbab5-150">Visual Studio projenizdeki tüm kodlar için varsayılan kök ad alanı olarak proje adınızı atar.</span><span class="sxs-lookup"><span data-stu-id="fbab5-150">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="fbab5-151">Örneğin, projeniz adlandırılmışsa, `ConsoleApplication1`programlama öğeleri ad `ConsoleApplication1`alanına aittir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-151">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="fbab5-152">Beyan `Namespace Magnetosphere`ederseniz, `Magnetosphere` projedeki başvurulara `ConsoleApplication1.Magnetosphere`erişecektir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-152">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="fbab5-153">Aşağıdaki örnekler, `Global` projenin kök ad alanı dışında bir ad alanı bildirmek için anahtar sözcüğü kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-153">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 <span data-ttu-id="fbab5-154">Ad alanı bildiriminde, `Global` başka bir ad alanında iç içe geçemez.</span><span class="sxs-lookup"><span data-stu-id="fbab5-154">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="fbab5-155">Projenin **Kök Ad Alanını** görüntülemek ve değiştirmek için Uygulama [Sayfasını, Proje Tasarımcısını (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-155">You can use the [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="fbab5-156">Yeni projeler için **Kök Ad Alanı** varsayılan olarak proje adına verilir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-156">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="fbab5-157">Üst `Global` düzey ad alanı olması **için,** kutuboş olacak şekilde Kök Ad Alanı girişini temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-157">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="fbab5-158">**Kök Ad Alanı'nın** temizlenmesi, `Global` ad alanı bildirimlerinde anahtar kelime gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-158">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="fbab5-159">Bir `Namespace` deyim .NET Framework'de de ad alanı olan bir ad bildirirse, `Global` anahtar kelime tam nitelikli bir adda kullanılmazsa .NET Framework ad alanı kullanılamaz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-159">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="fbab5-160">Anahtar kelimeyi `Global` kullanmadan bu .NET Framework ad alanına erişimi `Global` etkinleştirmek `Namespace` için, ekstredeki anahtar kelimeyi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-160">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="fbab5-161">Aşağıdaki örnekte `Global` `System.Text` ad alanı bildiriminde anahtar sözcük vardır.</span><span class="sxs-lookup"><span data-stu-id="fbab5-161">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="fbab5-162">`Global` Anahtar sözcük ad alanı bildiriminde yoksa, <xref:System.Text.StringBuilder> belirtmeden `Global.System.Text.StringBuilder`erişilemedi.</span><span class="sxs-lookup"><span data-stu-id="fbab5-162">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="fbab5-163">Adlı `ConsoleApplication1`bir proje `System.Text` için, `ConsoleApplication1.System.Text` `Global` anahtar kelime kullanılmamışsa başvurular erişilir.</span><span class="sxs-lookup"><span data-stu-id="fbab5-163">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="fbab5-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbab5-164">See also</span></span>

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [<span data-ttu-id="fbab5-165">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="fbab5-165">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="fbab5-166">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="fbab5-166">References and the Imports Statement</span></span>](references-and-the-imports-statement.md)
- [<span data-ttu-id="fbab5-167">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="fbab5-167">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="fbab5-168">Office Çözümlerinde Kod Yazma</span><span class="sxs-lookup"><span data-stu-id="fbab5-168">Writing Code in Office Solutions</span></span>](/visualstudio/vsto/writing-code-in-office-solutions)
