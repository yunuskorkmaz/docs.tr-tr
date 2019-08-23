---
title: My. Forms nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9fa5c77dd12c98100e3d17fc473a6802180d1e32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965978"
---
# <a name="myforms-object"></a><span data-ttu-id="49467-102">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="49467-102">My.Forms Object</span></span>
<span data-ttu-id="49467-103">Geçerli projede belirtilen her bir Windows formunun örneğine erişim için özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="49467-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49467-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49467-104">Remarks</span></span>  
 <span data-ttu-id="49467-105">Nesnesi `My.Forms` , geçerli projede her formun bir örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="49467-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="49467-106">Özelliğin adı, özelliğin eriştiği form adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="49467-106">The name of the property is the same as the name of the form that the property accesses.</span></span>   
  
 <span data-ttu-id="49467-107">`My.Forms` Nesne tarafından sunulan formlara, nitelik olmadan formun adını kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49467-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="49467-108">Özellik adı formun tür adıyla aynı olduğundan, bir forma varsayılan bir örnek olsa da erişmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="49467-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="49467-109">Örneğin, `My.Forms.Form1.Show` öğesine `Form1.Show`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="49467-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="49467-110">`My.Forms` Nesne yalnızca geçerli projeyle ilişkili formları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="49467-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="49467-111">Başvurulan DLL 'lerde belirtilen formlara erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="49467-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="49467-112">Bir DLL 'nin sağladığı bir forma erişmek için, formun adı dll olarak yazılmış şekilde tam adını kullanmanız gerekir. *FormName*.</span><span class="sxs-lookup"><span data-stu-id="49467-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="49467-113">Tüm uygulamanın açık formlarının <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> bir koleksiyonunu almak için özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49467-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="49467-114">Nesnesi ve özellikleri yalnızca Windows uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="49467-114">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="49467-115">Özellikler</span><span class="sxs-lookup"><span data-stu-id="49467-115">Properties</span></span>  
 <span data-ttu-id="49467-116">`My.Forms` Nesnesinin her özelliği, geçerli projedeki bir form örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="49467-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="49467-117">Özelliğin adı, özelliğin eriştiği form adı ile aynıdır ve özellik türü formun türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="49467-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49467-118">Bir ad çakışması varsa, bir forma erişmek için özellik adı,\_ *RootNamespace*_ ad alanı*FormName*olur.</span><span class="sxs-lookup"><span data-stu-id="49467-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="49467-119">Örneğin, bu formlardan biri kök ad `Form1.` `WindowsApplication1` alanında ve ad `Namespace1`alanında olduğunda, bu formdan `My.Forms.WindowsApplication1_Namespace1_Form1`' a eriştiğinizde adlı iki formu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="49467-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="49467-120">`My.Forms` Nesnesi, başlangıçta oluşturulan uygulamanın ana formunun örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="49467-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="49467-121">Diğer tüm formlarda, `My.Forms` nesne erişildiğinde formun yeni bir örneğini oluşturur ve depolar.</span><span class="sxs-lookup"><span data-stu-id="49467-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="49467-122">Bu özelliğe daha sonra erişme girişimleri, formun bu örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="49467-122">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="49467-123">Form için özelliğine atayarak `Nothing` formu atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49467-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="49467-124">Özellik ayarlayıcısı formun <xref:System.Windows.Forms.Form.Close%2A> yöntemini çağırır ve ardından depolanan değere atar `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="49467-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="49467-125">Özelliği dışında bir değer `Nothing` atarsanız, ayarlayıcı bir <xref:System.ArgumentException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="49467-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="49467-126">Bir `My.Forms` nesnenin özelliğinin, `Is` veya `IsNot` işlecini kullanarak formun bir örneğini depolayıp depomadığını test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49467-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="49467-127">Özelliğin değerinin olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="49467-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49467-128">Genellikle, `Is` veya `IsNot` işlecinin karşılaştırmayı gerçekleştirmek için özelliğinin değerini okuması gerekir.</span><span class="sxs-lookup"><span data-stu-id="49467-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="49467-129">Ancak, özelliği şu anda depoluyorsa `Nothing`, özelliği formun yeni bir örneğini oluşturur ve sonra bu örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="49467-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="49467-130">Ancak, Visual Basic Derleyicisi `My.Forms` nesnenin özelliklerini farklı şekilde değerlendirir ve `Is` veya `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="49467-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49467-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="49467-131">Example</span></span>  
 <span data-ttu-id="49467-132">Bu örnek, varsayılan `SidebarMenu` formun başlığını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="49467-132">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 <span data-ttu-id="49467-133">Bu örneğin çalışması için projenizin adında `SidebarMenu`bir form olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="49467-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>  
  
 <span data-ttu-id="49467-134">Bu kod, yalnızca bir Windows uygulama projesinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="49467-134">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49467-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49467-135">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="49467-136">Proje Türüne Göre Kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="49467-136">Availability by Project Type</span></span>  
  
|<span data-ttu-id="49467-137">Proje türü</span><span class="sxs-lookup"><span data-stu-id="49467-137">Project type</span></span>|<span data-ttu-id="49467-138">Kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="49467-138">Available</span></span>|  
|---|---|  
|<span data-ttu-id="49467-139">Windows uygulaması</span><span class="sxs-lookup"><span data-stu-id="49467-139">Windows Application</span></span>|<span data-ttu-id="49467-140">**Evet**</span><span class="sxs-lookup"><span data-stu-id="49467-140">**Yes**</span></span>|  
|<span data-ttu-id="49467-141">Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="49467-141">Class Library</span></span>|<span data-ttu-id="49467-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="49467-142">No</span></span>|  
|<span data-ttu-id="49467-143">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="49467-143">Console Application</span></span>|<span data-ttu-id="49467-144">Hayır</span><span class="sxs-lookup"><span data-stu-id="49467-144">No</span></span>|  
|<span data-ttu-id="49467-145">Windows Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="49467-145">Windows Control Library</span></span>|<span data-ttu-id="49467-146">Hayır</span><span class="sxs-lookup"><span data-stu-id="49467-146">No</span></span>|  
|<span data-ttu-id="49467-147">Web Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="49467-147">Web Control Library</span></span>|<span data-ttu-id="49467-148">Hayır</span><span class="sxs-lookup"><span data-stu-id="49467-148">No</span></span>|  
|<span data-ttu-id="49467-149">Windows Hizmeti</span><span class="sxs-lookup"><span data-stu-id="49467-149">Windows Service</span></span>|<span data-ttu-id="49467-150">Hayır</span><span class="sxs-lookup"><span data-stu-id="49467-150">No</span></span>|  
|<span data-ttu-id="49467-151">Web Sitesi</span><span class="sxs-lookup"><span data-stu-id="49467-151">Web Site</span></span>|<span data-ttu-id="49467-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="49467-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49467-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49467-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="49467-154">Nesneler</span><span class="sxs-lookup"><span data-stu-id="49467-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)
- [<span data-ttu-id="49467-155">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="49467-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="49467-156">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="49467-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="49467-157">Uygulama Formlarına Erişme</span><span class="sxs-lookup"><span data-stu-id="49467-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
