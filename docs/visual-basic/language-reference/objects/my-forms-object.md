---
title: My.Forms Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 001f6fbfae2467ea0af5e98ca041b694d1e7b8f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372446"
---
# <a name="myforms-object"></a><span data-ttu-id="06d61-102">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="06d61-102">My.Forms Object</span></span>

<span data-ttu-id="06d61-103">Geçerli projede belirtilen her bir Windows formunun örneğine erişim için özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="06d61-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>

## <a name="remarks"></a><span data-ttu-id="06d61-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06d61-104">Remarks</span></span>

<span data-ttu-id="06d61-105">`My.Forms`Nesnesi, geçerli projede her formun bir örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="06d61-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="06d61-106">Özelliğin adı, özelliğin eriştiği form adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="06d61-106">The name of the property is the same as the name of the form that the property accesses.</span></span>

<span data-ttu-id="06d61-107">Nesne tarafından sunulan formlara `My.Forms` , nitelik olmadan formun adını kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06d61-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="06d61-108">Özellik adı formun tür adıyla aynı olduğundan, bir forma varsayılan bir örnek olsa da erişmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="06d61-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="06d61-109">Örneğin, `My.Forms.Form1.Show` öğesine eşdeğerdir `Form1.Show` .</span><span class="sxs-lookup"><span data-stu-id="06d61-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>

<span data-ttu-id="06d61-110">`My.Forms`Nesne yalnızca geçerli projeyle ilişkili formları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="06d61-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="06d61-111">Başvurulan DLL 'lerde belirtilen formlara erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="06d61-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="06d61-112">Bir DLL 'nin sağladığı bir forma erişmek için, formun adı dll olarak *yazılmış şekilde tam*adını kullanmanız gerekir. *FormName*.</span><span class="sxs-lookup"><span data-stu-id="06d61-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>

<span data-ttu-id="06d61-113"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>Tüm uygulamanın açık formlarının bir koleksiyonunu almak için özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06d61-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>

<span data-ttu-id="06d61-114">Nesnesi ve özellikleri yalnızca Windows uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06d61-114">The object and its properties are available only for Windows applications.</span></span>

## <a name="properties"></a><span data-ttu-id="06d61-115">Özellikler</span><span class="sxs-lookup"><span data-stu-id="06d61-115">Properties</span></span>

<span data-ttu-id="06d61-116">Nesnesinin her özelliği, `My.Forms` geçerli projedeki bir form örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="06d61-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="06d61-117">Özelliğin adı, özelliğin eriştiği form adı ile aynıdır ve özellik türü formun türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="06d61-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>

> [!NOTE]
> <span data-ttu-id="06d61-118">Bir ad çakışması varsa, bir forma erişmek için özellik adı, *RootNamespace\*\*_ ad alanı* \_ *FormName*olur.</span><span class="sxs-lookup"><span data-stu-id="06d61-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="06d61-119">Örneğin, `Form1.` Bu formlardan biri kök ad alanında `WindowsApplication1` ve ad alanında olduğunda, bu `Namespace1` formdan ' a eriştiğinizde adlı iki formu göz önünde bulundurun `My.Forms.WindowsApplication1_Namespace1_Form1` .</span><span class="sxs-lookup"><span data-stu-id="06d61-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>

<span data-ttu-id="06d61-120">`My.Forms`Nesnesi, başlangıçta oluşturulan uygulamanın ana formunun örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="06d61-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="06d61-121">Diğer tüm formlarda, `My.Forms` nesne erişildiğinde formun yeni bir örneğini oluşturur ve depolar.</span><span class="sxs-lookup"><span data-stu-id="06d61-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="06d61-122">Bu özelliğe daha sonra erişme girişimleri, formun bu örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="06d61-122">Subsequent attempts to access that property return that instance of the form.</span></span>

<span data-ttu-id="06d61-123">Form için özelliğine atayarak formu atabilirsiniz `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="06d61-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="06d61-124">Özellik ayarlayıcısı <xref:System.Windows.Forms.Form.Close%2A> formun yöntemini çağırır ve ardından `Nothing` depolanan değere atar.</span><span class="sxs-lookup"><span data-stu-id="06d61-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="06d61-125">Özelliği dışında bir değer atarsanız `Nothing` , ayarlayıcı bir <xref:System.ArgumentException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06d61-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="06d61-126">Bir `My.Forms` nesnenin özelliğinin, veya işlecini kullanarak formun bir örneğini depolayıp depomadığını test edebilirsiniz `Is` `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="06d61-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="06d61-127">Özelliğin değerinin olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="06d61-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>

> [!NOTE]
> <span data-ttu-id="06d61-128">Genellikle, `Is` veya `IsNot` işlecinin karşılaştırmayı gerçekleştirmek için özelliğinin değerini okuması gerekir.</span><span class="sxs-lookup"><span data-stu-id="06d61-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="06d61-129">Ancak, özelliği şu anda depoluyorsa `Nothing` , özelliği formun yeni bir örneğini oluşturur ve sonra bu örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="06d61-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="06d61-130">Ancak, Visual Basic Derleyicisi `My.Forms` nesnenin özelliklerini farklı şekilde değerlendirir ve `Is` veya `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="06d61-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>

## <a name="example"></a><span data-ttu-id="06d61-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="06d61-131">Example</span></span>

<span data-ttu-id="06d61-132">Bu örnek, varsayılan formun başlığını değiştirir `SidebarMenu` .</span><span class="sxs-lookup"><span data-stu-id="06d61-132">This example changes the title of the default `SidebarMenu` form.</span></span>

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

<span data-ttu-id="06d61-133">Bu örneğin çalışması için projenizin adında bir form olması gerekir `SidebarMenu` .</span><span class="sxs-lookup"><span data-stu-id="06d61-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>

<span data-ttu-id="06d61-134">Bu kod, yalnızca bir Windows uygulama projesinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="06d61-134">This code will work only in a Windows Application project.</span></span>

## <a name="requirements"></a><span data-ttu-id="06d61-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06d61-135">Requirements</span></span>

### <a name="availability-by-project-type"></a><span data-ttu-id="06d61-136">Proje Türüne Göre Kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="06d61-136">Availability by Project Type</span></span>

|<span data-ttu-id="06d61-137">Proje türü</span><span class="sxs-lookup"><span data-stu-id="06d61-137">Project type</span></span>|<span data-ttu-id="06d61-138">Kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="06d61-138">Available</span></span>|
|---|---|
|<span data-ttu-id="06d61-139">Windows uygulaması</span><span class="sxs-lookup"><span data-stu-id="06d61-139">Windows Application</span></span>|<span data-ttu-id="06d61-140">**Evet**</span><span class="sxs-lookup"><span data-stu-id="06d61-140">**Yes**</span></span>|
|<span data-ttu-id="06d61-141">Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="06d61-141">Class Library</span></span>|<span data-ttu-id="06d61-142">No</span><span class="sxs-lookup"><span data-stu-id="06d61-142">No</span></span>|
|<span data-ttu-id="06d61-143">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="06d61-143">Console Application</span></span>|<span data-ttu-id="06d61-144">No</span><span class="sxs-lookup"><span data-stu-id="06d61-144">No</span></span>|
|<span data-ttu-id="06d61-145">Windows Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="06d61-145">Windows Control Library</span></span>|<span data-ttu-id="06d61-146">No</span><span class="sxs-lookup"><span data-stu-id="06d61-146">No</span></span>|
|<span data-ttu-id="06d61-147">Web Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="06d61-147">Web Control Library</span></span>|<span data-ttu-id="06d61-148">No</span><span class="sxs-lookup"><span data-stu-id="06d61-148">No</span></span>|
|<span data-ttu-id="06d61-149">Windows Hizmeti</span><span class="sxs-lookup"><span data-stu-id="06d61-149">Windows Service</span></span>|<span data-ttu-id="06d61-150">No</span><span class="sxs-lookup"><span data-stu-id="06d61-150">No</span></span>|
|<span data-ttu-id="06d61-151">Web Sitesi</span><span class="sxs-lookup"><span data-stu-id="06d61-151">Web Site</span></span>|<span data-ttu-id="06d61-152">No</span><span class="sxs-lookup"><span data-stu-id="06d61-152">No</span></span>|

## <a name="see-also"></a><span data-ttu-id="06d61-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06d61-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="06d61-154">Nesneler</span><span class="sxs-lookup"><span data-stu-id="06d61-154">Objects</span></span>](index.md)
- [<span data-ttu-id="06d61-155">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="06d61-155">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="06d61-156">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="06d61-156">IsNot Operator</span></span>](../operators/isnot-operator.md)
- [<span data-ttu-id="06d61-157">Uygulama Formlarına Erişme</span><span class="sxs-lookup"><span data-stu-id="06d61-157">Accessing Application Forms</span></span>](../../developing-apps/programming/accessing-application-forms.md)
