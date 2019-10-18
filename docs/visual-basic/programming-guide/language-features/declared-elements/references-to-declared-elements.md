---
title: Bildirilmiş Öğelere Başvurular (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: de4d42803be48a87f4dfd37a92b1b22fa2d5c554
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524561"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="18f53-102">Bildirilmiş Öğelere Başvurular (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18f53-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="18f53-103">Kodunuz, belirtilen bir öğeye başvurduğunda, Visual Basic derleyici, bu adın uygun bildirimine başvurinizdeki adla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="18f53-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="18f53-104">Aynı ada sahip birden fazla öğe bildirilirse, adını *niteleyerek* bu öğelerin ne şekilde başvurulduğunu kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="18f53-105">Derleyici, bir ad başvurusunu en *dar kapsamlı*bir ad bildirimine eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="18f53-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="18f53-106">Bu, başvuru yapan kod ile başladığı ve kapsayan öğelerin birbirini izleyen düzeylerinde dışa doğru çalışacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="18f53-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="18f53-107">Aşağıdaki örnek, aynı ada sahip iki değişkene yapılan başvuruları gösterir.</span><span class="sxs-lookup"><span data-stu-id="18f53-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="18f53-108">Örnek, her bir `totalCount`, modül `container` farklı kapsam düzeylerindeki iki değişken bildirir.</span><span class="sxs-lookup"><span data-stu-id="18f53-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="18f53-109">Yordam `showCount`, nitelendirme olmadan `totalCount` görüntülüyorsa Visual Basic derleyici, en dar kapsamı olan bildirime başvuruyu çözer, yani `showCount` içindeki yerel bildirim.</span><span class="sxs-lookup"><span data-stu-id="18f53-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="18f53-110">@No__t_0, kapsayan modül `container` ile nitelediğinde, derleyici daha geniş kapsamlı bir bildirime başvuruyu çözer.</span><span class="sxs-lookup"><span data-stu-id="18f53-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="18f53-111">Öğe adını nitelendirme</span><span class="sxs-lookup"><span data-stu-id="18f53-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="18f53-112">Bu arama işlemini geçersiz kılmak ve daha geniş bir kapsamda belirtilen bir ad belirtmek istiyorsanız, adı daha geniş kapsamın kapsayan öğesiyle *nitelemeniz* gerekir.</span><span class="sxs-lookup"><span data-stu-id="18f53-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="18f53-113">Bazı durumlarda, kapsayan öğesini de nitelemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="18f53-114">Bir adın nitelemesini, kaynak deyiminizde, hedef öğenin nerede tanımlandığını tanımlayan bilgilerle daha önce anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="18f53-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="18f53-115">Bu bilgilere bir *nitelik dizesi*adı verilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="18f53-116">Bir veya daha fazla ad alanı ve bir modül, sınıf ya da yapı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="18f53-117">Nitelik dizesi, hedef öğeyi içeren modülü, sınıfı veya yapıyı kesin olarak belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="18f53-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="18f53-118">Kapsayıcı, genellikle bir ad alanı olan başka bir kapsayan öğede bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="18f53-119">Nitelik dizesinde içerilen birkaç öğe eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="18f53-120">Adı niteleyerek, belirtilen bir öğeye erişmek için</span><span class="sxs-lookup"><span data-stu-id="18f53-120">To access a declared element by qualifying its name</span></span>  
  
1. <span data-ttu-id="18f53-121">Öğenin tanımlandığı konumu saptayın.</span><span class="sxs-lookup"><span data-stu-id="18f53-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="18f53-122">Bu, bir ad alanı ya da bir ad uzayı hiyerarşisi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="18f53-123">En düşük düzey ad alanı içinde, öğe bir modül, sınıf veya yapıda bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18f53-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. <span data-ttu-id="18f53-124">Hedef öğenin konumuna göre bir nitelik yolu belirleme.</span><span class="sxs-lookup"><span data-stu-id="18f53-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="18f53-125">En üst düzey ad alanıyla başlayın, en düşük düzey ad alanına ilerleyin ve hedef öğeyi içeren modül, sınıf ya da yapıyla sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="18f53-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="18f53-126">Yoldaki her öğe, takip eden öğesi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="18f53-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="18f53-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="18f53-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3. <span data-ttu-id="18f53-128">Hedef öğe için nitelik dizesini hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="18f53-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="18f53-129">Yoldaki her öğeden sonra bir nokta (`.`) koyun.</span><span class="sxs-lookup"><span data-stu-id="18f53-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="18f53-130">Uygulamanızın, nitelik dizinizdeki her öğeye erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18f53-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. <span data-ttu-id="18f53-131">Hedef öğeye başvuran ifade veya atama deyimini normal şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="18f53-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. <span data-ttu-id="18f53-132">Hedef öğe adından önce nitelik dizesiyle önce.</span><span class="sxs-lookup"><span data-stu-id="18f53-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="18f53-133">Ad, öğeyi içeren modülü, sınıfı ya da yapıyı izleyen süreyi (`.`) hemen izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="18f53-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. <span data-ttu-id="18f53-134">Derleyici, hedef öğe başvurusuyla eşleşlebileceği açık, belirsiz bir bildirim bulmak için nitelik dizesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="18f53-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="18f53-135">Ayrıca, uygulamanızın aynı ada sahip birden fazla programlama öğesine erişimi varsa, bir ad başvurusunu nitelemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="18f53-136">Örneğin, <xref:System.Windows.Forms> ve <xref:System.Web.UI.WebControls> ad alanları, bir `Label` sınıfı (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> ve <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>) içerir.</span><span class="sxs-lookup"><span data-stu-id="18f53-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="18f53-137">Uygulamanız her ikisini de kullanıyorsa veya kendi `Label` sınıfını tanımlıyorsa, farklı `Label` nesnelerini ayırt etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="18f53-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="18f53-138">Ad alanını veya içeri aktarma diğer adını değişken bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="18f53-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="18f53-139">Aşağıdaki örnek, içeri aktarma diğer adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="18f53-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="18f53-140">Diğer öğeleri Içeren Üyeler</span><span class="sxs-lookup"><span data-stu-id="18f53-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="18f53-141">Başka bir sınıfın veya yapının paylaşılmayan bir üyesini kullandığınızda, önce üye adını bir sınıf veya yapının örneğine işaret eden bir değişkenle veya ifadeyle nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="18f53-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="18f53-142">Aşağıdaki örnekte, `demoClass` `class1` adlı bir sınıfın örneğidir.</span><span class="sxs-lookup"><span data-stu-id="18f53-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="18f53-143">[Paylaşılmayan](../../../../visual-basic/language-reference/modifiers/shared.md)bir üyeyi nitelemek için sınıf adının kendisini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="18f53-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="18f53-144">Önce bir nesne değişkeninde bir örnek oluşturmanız gerekir (Bu durumda `demoClass`) ve ardından değişken adına göre başvurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="18f53-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="18f53-145">Bir sınıf veya yapının `Shared` üyesi varsa, bu üyeyi sınıf veya yapı adıyla veya bir örneğe işaret eden bir değişkenle ya da ifadeyle niteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="18f53-146">Bir modül ayrı örneklere sahip değildir ve tüm üyeleri varsayılan olarak `Shared`.</span><span class="sxs-lookup"><span data-stu-id="18f53-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="18f53-147">Bu nedenle bir modül üyesini modül adıyla niteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="18f53-148">Aşağıdaki örnek, modül üye yordamlarına nitelikli başvuruları gösterir.</span><span class="sxs-lookup"><span data-stu-id="18f53-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="18f53-149">Örnek, hem `perform` hem de bir projedeki farklı modüllerde bulunan iki `Sub` yordamlarını bildirir.</span><span class="sxs-lookup"><span data-stu-id="18f53-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="18f53-150">Her biri kendi modülünde nitelenmeden belirlenebilir, ancak başka herhangi bir yerden başvuruluyorsa nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="18f53-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="18f53-151">@No__t_0 içindeki son başvuru `perform` uygun olmadığından, derleyici bu başvuruyu çözemez.</span><span class="sxs-lookup"><span data-stu-id="18f53-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="18f53-152">Projelere başvurular</span><span class="sxs-lookup"><span data-stu-id="18f53-152">References to Projects</span></span>  
 <span data-ttu-id="18f53-153">Başka bir projede tanımlanmış [ortak](../../../../visual-basic/language-reference/modifiers/public.md) öğeleri kullanmak için, önce bu projenin derlemesine veya tür kitaplığına bir *başvuru* ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18f53-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="18f53-154">Bir başvuru ayarlamak için **Proje** menüsünde **Başvuru Ekle** ' ye tıklayın veya [-Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) komut satırı derleyici seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="18f53-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [-reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="18f53-155">Örneğin, .NET Framework XML nesne modelini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-155">For example, you can use the XML object model of the .NET Framework.</span></span> <span data-ttu-id="18f53-156">@No__t_0 ad alanına bir başvuru ayarlarsanız, <xref:System.Xml.XmlDocument> gibi sınıflarından herhangi birini bildirebilir ve kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="18f53-157">Aşağıdaki örnek <xref:System.Xml.XmlDocument> kullanır.</span><span class="sxs-lookup"><span data-stu-id="18f53-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="18f53-158">Içerilen öğeleri içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="18f53-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="18f53-159">Kullanmak istediğiniz modülleri veya sınıfları içeren ad alanlarını *içeri aktarmak* Için [Imports Ifadesini (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="18f53-160">Bu, adlarını tamamen nitelemeden içeri aktarılan bir ad alanında tanımlanan öğelere başvurmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="18f53-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="18f53-161">Aşağıdaki örnek, <xref:System.Xml> ad alanını içeri aktarmak için önceki örneği yeniden yazar.</span><span class="sxs-lookup"><span data-stu-id="18f53-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="18f53-162">Ayrıca, `Imports` ifade, içeri aktarılan her ad alanı için bir *içeri aktarma diğer adı* tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="18f53-163">Bu, kaynak kodu daha kısa ve daha kolay okunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="18f53-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="18f53-164">Aşağıdaki örnek, <xref:System.Xml> ad alanı için bir diğer ad olarak `xD` kullanmak için önceki örneği yeniden yazar.</span><span class="sxs-lookup"><span data-stu-id="18f53-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="18f53-165">@No__t_0 ifade, uygulamanız için kullanılabilir olan diğer projelerden öğe yapmaz.</span><span class="sxs-lookup"><span data-stu-id="18f53-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="18f53-166">Diğer bir deyişle, bir başvuru ayarlamanın yerini almaz.</span><span class="sxs-lookup"><span data-stu-id="18f53-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="18f53-167">Bir ad alanını içeri aktarmak, bu ad alanında tanımlanan adları nitelendirmek için gereken gereksinimi ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="18f53-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="18f53-168">Ayrıca, modülleri, sınıfları, yapıları ve numaralandırmalar içeri aktarmak için `Imports` ifadesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="18f53-169">Daha sonra, bu içeri aktarılan öğelerin üyelerini nitelik olmadan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="18f53-170">Ancak, sınıfların ve yapıların paylaşılmayan üyelerini her zaman, sınıf veya yapının bir örneğini değerlendiren bir değişkenle veya ifadeyle nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="18f53-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="18f53-171">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="18f53-171">Naming Guidelines</span></span>  
 <span data-ttu-id="18f53-172">Aynı ada sahip iki veya daha fazla programlama öğesi tanımladığınızda, derleyici bu ada bir başvuruyu çözmeyi denediğinde bir *ad belirsizliğe* neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="18f53-173">Kapsam içinde birden fazla tanım varsa veya kapsam içinde bir tanım yoksa, başvuru ırıolarak çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="18f53-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="18f53-174">Bir örnek için, bu Yardım sayfasında "nitelikli başvuru örneği" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="18f53-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="18f53-175">Tüm öğelerinizi benzersiz adlara vererek ad belirsizliğe engel olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="18f53-176">Daha sonra, adını bir ad alanı, modül veya sınıf ile nitelendirmek zorunda kalmadan herhangi bir öğeye başvuru yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="18f53-177">Yanlışlıkla yanlış öğeye başvurma olasılığını da azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18f53-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="18f53-178">Gölge Kullanım</span><span class="sxs-lookup"><span data-stu-id="18f53-178">Shadowing</span></span>  
 <span data-ttu-id="18f53-179">İki programlama öğesi aynı adı paylaşıyorsa, bunlardan biri diğer birini gizleyebilir veya *gölgelendirebilir*.</span><span class="sxs-lookup"><span data-stu-id="18f53-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="18f53-180">Gölgelendirilmiş bir öğe başvuru için kullanılamaz; Bunun yerine, kodunuz gölgeli öğe adını kullandığında, Visual Basic derleyici onu gölgeleme öğesine çözer.</span><span class="sxs-lookup"><span data-stu-id="18f53-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="18f53-181">Örneklerle ilgili daha ayrıntılı bir açıklama için bkz. [gölgeleme Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="18f53-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f53-182">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18f53-182">See also</span></span>

- [<span data-ttu-id="18f53-183">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="18f53-183">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="18f53-184">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="18f53-184">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="18f53-185">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="18f53-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="18f53-186">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="18f53-186">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="18f53-187">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="18f53-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="18f53-188">New İşleci</span><span class="sxs-lookup"><span data-stu-id="18f53-188">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="18f53-189">Public</span><span class="sxs-lookup"><span data-stu-id="18f53-189">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
