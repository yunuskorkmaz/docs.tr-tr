---
title: My.Forms Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: db86704fdc8120ccac5f4489c80a515834ad888f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350368"
---
# <a name="myforms-object"></a><span data-ttu-id="b02f6-102">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="b02f6-102">My.Forms Object</span></span>

<span data-ttu-id="b02f6-103">Geçerli projede belirtilen her bir Windows formunun örneğine erişim için özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b02f6-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>

## <a name="remarks"></a><span data-ttu-id="b02f6-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b02f6-104">Remarks</span></span>

<span data-ttu-id="b02f6-105">`My.Forms` nesnesi, geçerli projede her formun bir örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b02f6-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="b02f6-106">Özelliğin adı, özelliğin eriştiği form adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b02f6-106">The name of the property is the same as the name of the form that the property accesses.</span></span>

<span data-ttu-id="b02f6-107">`My.Forms` nesnesi tarafından sunulan formlara, nitelik olmadan formun adını kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02f6-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="b02f6-108">Özellik adı formun tür adıyla aynı olduğundan, bir forma varsayılan bir örnek olsa da erişmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="b02f6-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="b02f6-109">Örneğin, `My.Forms.Form1.Show` `Form1.Show`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b02f6-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>

<span data-ttu-id="b02f6-110">`My.Forms` nesnesi yalnızca geçerli projeyle ilişkili formları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="b02f6-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="b02f6-111">Başvurulan DLL 'lerde belirtilen formlara erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b02f6-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="b02f6-112">Bir DLL 'nin sağladığı bir forma erişmek için, formun adı dll olarak *yazılmış şekilde tam*adını kullanmanız gerekir. *FormName*.</span><span class="sxs-lookup"><span data-stu-id="b02f6-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>

<span data-ttu-id="b02f6-113">Tüm uygulamaların açık formlarının bir koleksiyonunu almak için <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02f6-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>

<span data-ttu-id="b02f6-114">Nesnesi ve özellikleri yalnızca Windows uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b02f6-114">The object and its properties are available only for Windows applications.</span></span>

## <a name="properties"></a><span data-ttu-id="b02f6-115">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b02f6-115">Properties</span></span>

<span data-ttu-id="b02f6-116">`My.Forms` nesnesinin her özelliği, geçerli projedeki bir form örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b02f6-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="b02f6-117">Özelliğin adı, özelliğin eriştiği form adı ile aynıdır ve özellik türü formun türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b02f6-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>

> [!NOTE]
> <span data-ttu-id="b02f6-118">Ad çakışması varsa, bir forma erişmek için özellik adı,\_*FormName*adlı *RootNamespace*_*ad* alanıdır.</span><span class="sxs-lookup"><span data-stu-id="b02f6-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="b02f6-119">Örneğin, bu formlardan biri kök ad alanında `WindowsApplication1` ve ad alanı `Namespace1``Form1.`adlı iki formu göz önünde bulundurun. Bu forma `My.Forms.WindowsApplication1_Namespace1_Form1`aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02f6-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>

<span data-ttu-id="b02f6-120">`My.Forms` nesnesi, başlangıçta oluşturulan uygulamanın ana formunun örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b02f6-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="b02f6-121">Tüm diğer formlar için `My.Forms` nesnesi, erişildiğinde formun yeni bir örneğini oluşturur ve depolar.</span><span class="sxs-lookup"><span data-stu-id="b02f6-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="b02f6-122">Bu özelliğe daha sonra erişme girişimleri, formun bu örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b02f6-122">Subsequent attempts to access that property return that instance of the form.</span></span>

<span data-ttu-id="b02f6-123">Bu formun özelliğine `Nothing` atayarak formu atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02f6-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="b02f6-124">Özellik ayarlayıcısı, formun <xref:System.Windows.Forms.Form.Close%2A> yöntemini çağırır ve sonra depolanan değere `Nothing` atar.</span><span class="sxs-lookup"><span data-stu-id="b02f6-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="b02f6-125">Özelliğe `Nothing` dışında herhangi bir değer atarsanız, ayarlayıcı bir <xref:System.ArgumentException> özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b02f6-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="b02f6-126">`My.Forms` nesnesinin bir özelliğinin, `Is` veya `IsNot` işlecini kullanarak formun bir örneğini depolayıp depoladığını test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02f6-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="b02f6-127">Bu işleçleri, özelliğin değerinin `Nothing`olup olmadığını denetlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b02f6-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>

> [!NOTE]
> <span data-ttu-id="b02f6-128">Genellikle, `Is` veya `IsNot` işleci, karşılaştırmayı gerçekleştirmek için özelliğinin değerini okumalı.</span><span class="sxs-lookup"><span data-stu-id="b02f6-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="b02f6-129">Ancak, özelliği şu anda `Nothing`depoluyorsa, özelliği formun yeni bir örneğini oluşturur ve sonra bu örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="b02f6-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="b02f6-130">Ancak, Visual Basic derleyici `My.Forms` nesnesinin özelliklerini farklı şekilde değerlendirir ve `Is` ya da `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b02f6-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>

## <a name="example"></a><span data-ttu-id="b02f6-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="b02f6-131">Example</span></span>

<span data-ttu-id="b02f6-132">Bu örnek, varsayılan `SidebarMenu` formun başlığını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b02f6-132">This example changes the title of the default `SidebarMenu` form.</span></span>

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

<span data-ttu-id="b02f6-133">Bu örneğin çalışması için, projenizin `SidebarMenu`adlı bir formu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b02f6-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>

<span data-ttu-id="b02f6-134">Bu kod, yalnızca bir Windows uygulama projesinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="b02f6-134">This code will work only in a Windows Application project.</span></span>

## <a name="requirements"></a><span data-ttu-id="b02f6-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b02f6-135">Requirements</span></span>

### <a name="availability-by-project-type"></a><span data-ttu-id="b02f6-136">Proje Türüne Göre Kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="b02f6-136">Availability by Project Type</span></span>

|<span data-ttu-id="b02f6-137">Proje türü</span><span class="sxs-lookup"><span data-stu-id="b02f6-137">Project type</span></span>|<span data-ttu-id="b02f6-138">Kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="b02f6-138">Available</span></span>|
|---|---|
|<span data-ttu-id="b02f6-139">Windows uygulaması</span><span class="sxs-lookup"><span data-stu-id="b02f6-139">Windows Application</span></span>|<span data-ttu-id="b02f6-140">**Yes**</span><span class="sxs-lookup"><span data-stu-id="b02f6-140">**Yes**</span></span>|
|<span data-ttu-id="b02f6-141">Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b02f6-141">Class Library</span></span>|<span data-ttu-id="b02f6-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="b02f6-142">No</span></span>|
|<span data-ttu-id="b02f6-143">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="b02f6-143">Console Application</span></span>|<span data-ttu-id="b02f6-144">Hayır</span><span class="sxs-lookup"><span data-stu-id="b02f6-144">No</span></span>|
|<span data-ttu-id="b02f6-145">Windows Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b02f6-145">Windows Control Library</span></span>|<span data-ttu-id="b02f6-146">Hayır</span><span class="sxs-lookup"><span data-stu-id="b02f6-146">No</span></span>|
|<span data-ttu-id="b02f6-147">Web Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b02f6-147">Web Control Library</span></span>|<span data-ttu-id="b02f6-148">Hayır</span><span class="sxs-lookup"><span data-stu-id="b02f6-148">No</span></span>|
|<span data-ttu-id="b02f6-149">Windows Hizmeti</span><span class="sxs-lookup"><span data-stu-id="b02f6-149">Windows Service</span></span>|<span data-ttu-id="b02f6-150">Hayır</span><span class="sxs-lookup"><span data-stu-id="b02f6-150">No</span></span>|
|<span data-ttu-id="b02f6-151">Web Sitesi</span><span class="sxs-lookup"><span data-stu-id="b02f6-151">Web Site</span></span>|<span data-ttu-id="b02f6-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="b02f6-152">No</span></span>|

## <a name="see-also"></a><span data-ttu-id="b02f6-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b02f6-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="b02f6-154">Nesneler</span><span class="sxs-lookup"><span data-stu-id="b02f6-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)
- [<span data-ttu-id="b02f6-155">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="b02f6-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="b02f6-156">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="b02f6-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="b02f6-157">Uygulama Formlarına Erişme</span><span class="sxs-lookup"><span data-stu-id="b02f6-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
