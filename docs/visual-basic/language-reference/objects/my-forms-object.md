---
title: My.Forms nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: d15765b7673f321d4362ceea0adb73959a7e7726
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582664"
---
# <a name="myforms-object"></a><span data-ttu-id="60019-102">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="60019-102">My.Forms Object</span></span>
<span data-ttu-id="60019-103">Geçerli projede bildirilen her Windows formunu örneğini erişmek için özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="60019-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60019-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60019-104">Remarks</span></span>  
 <span data-ttu-id="60019-105">`My.Forms` Nesne örneği geçerli projedeki her bir form sağlar.</span><span class="sxs-lookup"><span data-stu-id="60019-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="60019-106">Özelliğin adı özelliği erişen adı ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="60019-106">The name of the property is the same as the name of the form that the property accesses.</span></span>   
  
 <span data-ttu-id="60019-107">Tarafından sağlanan forms erişebileceğiniz `My.Forms` nitelik olmadan formun adını kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="60019-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="60019-108">Özellik adı, formun tür adıyla aynı olduğundan, bu varsayılan bir örnek varmış gibi bir form erişmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="60019-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="60019-109">Örneğin, `My.Forms.Form1.Show` eşdeğerdir `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="60019-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="60019-110">`My.Forms` Nesnesi yalnızca geçerli projeyle ilişkili formları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="60019-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="60019-111">DLL içinde bildirilen formlara erişimi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="60019-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="60019-112">Bir DLL sağlayan bir forma erişmek için tam olarak yazılan formun adını kullanın *dll*. *Formadı*.</span><span class="sxs-lookup"><span data-stu-id="60019-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="60019-113">Kullanabileceğiniz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> uygulamanın tüm açık form koleksiyonu alınacağı özellik.</span><span class="sxs-lookup"><span data-stu-id="60019-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="60019-114">Nesne ve özellikleri, yalnızca Windows uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="60019-114">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="60019-115">Özellikler</span><span class="sxs-lookup"><span data-stu-id="60019-115">Properties</span></span>  
 <span data-ttu-id="60019-116">Her bir özelliği `My.Forms` nesnesi geçerli proje içinde bir formun örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="60019-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="60019-117">Özelliğin adı özelliği erişen adı ile aynıdır ve özellik türü form denetiminin türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="60019-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60019-118">Bir ad çakışması varsa, bir forma erişmek için özellik adı olan *RootNamespace*_*Namespace*\_*formadı*.</span><span class="sxs-lookup"><span data-stu-id="60019-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="60019-119">Örneğin, iki forms adlı göz önünde bulundurun `Form1.`biçimlerinden kök ad alanında olup olmadığını `WindowsApplication1` ve ad alanındaki `Namespace1`, bu formu üzerinden eriştiğiniz `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="60019-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="60019-120">`My.Forms` Nesnesi başlangıç sırasında oluşturulan uygulamanın ana formu örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="60019-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="60019-121">Diğer tüm biçimler için `My.Forms` nesnesi erişilir ve depolar, formun yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="60019-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="60019-122">Bu özelliğe erişmek için sonraki denemeler form örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="60019-122">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="60019-123">Atayarak bir formu dispose `Nothing` özelliğine oluşturan.</span><span class="sxs-lookup"><span data-stu-id="60019-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="60019-124">Özellik ayarlayıcı çağrılarında <xref:System.Windows.Forms.Form.Close%2A> form ve ardından atar yöntemi `Nothing` depolanmış değere.</span><span class="sxs-lookup"><span data-stu-id="60019-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="60019-125">Dışında herhangi bir değer atamanız durumunda `Nothing` ayarlayıcı özelliğine atar bir <xref:System.ArgumentException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="60019-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="60019-126">Bir özelliği olup olmadığını sınayabilirsiniz `My.Forms` nesneyi kullanarak bir formun örneğini depolar `Is` veya `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="60019-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="60019-127">Bu işleçler özelliğinin değeri olup olmadığını denetlemek için kullanabileceğiniz `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="60019-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60019-128">Genellikle, `Is` veya `IsNot` işleci olan bir karşılaştırma yapmak için özelliğinin değeri okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="60019-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="60019-129">Ancak, bu özellik şu anda depoluyorsa `Nothing`, özellik formun yeni bir örneğini oluşturur ve bu örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="60019-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="60019-130">Ancak, Visual Basic derleyici özelliklerini işler `My.Forms` sağlar ve farklı nesne `Is` veya `IsNot` değerini değiştirmeden özelliğinin durumu denetlemek için işleci.</span><span class="sxs-lookup"><span data-stu-id="60019-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60019-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="60019-131">Example</span></span>  
 <span data-ttu-id="60019-132">Bu örnekte varsayılan başlığın değiştiğine `SidebarMenu` formu.</span><span class="sxs-lookup"><span data-stu-id="60019-132">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="60019-133">Çalışmak bu örnek için projenizde adlı bir form olmalı `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="60019-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>  
  
 <span data-ttu-id="60019-134">Bu kod yalnızca bir Windows uygulaması projesi içinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="60019-134">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60019-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60019-135">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="60019-136">Proje Türüne Göre Kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="60019-136">Availability by Project Type</span></span>  
  
|<span data-ttu-id="60019-137">Proje türü</span><span class="sxs-lookup"><span data-stu-id="60019-137">Project type</span></span>|<span data-ttu-id="60019-138">Kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="60019-138">Available</span></span>|  
|---|---|  
|<span data-ttu-id="60019-139">Windows uygulama</span><span class="sxs-lookup"><span data-stu-id="60019-139">Windows Application</span></span>|<span data-ttu-id="60019-140">**Evet**</span><span class="sxs-lookup"><span data-stu-id="60019-140">**Yes**</span></span>|  
|<span data-ttu-id="60019-141">Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="60019-141">Class Library</span></span>|<span data-ttu-id="60019-142">Hayır</span><span class="sxs-lookup"><span data-stu-id="60019-142">No</span></span>|  
|<span data-ttu-id="60019-143">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="60019-143">Console Application</span></span>|<span data-ttu-id="60019-144">Hayır</span><span class="sxs-lookup"><span data-stu-id="60019-144">No</span></span>|  
|<span data-ttu-id="60019-145">Windows Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="60019-145">Windows Control Library</span></span>|<span data-ttu-id="60019-146">Hayır</span><span class="sxs-lookup"><span data-stu-id="60019-146">No</span></span>|  
|<span data-ttu-id="60019-147">Web Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="60019-147">Web Control Library</span></span>|<span data-ttu-id="60019-148">Hayır</span><span class="sxs-lookup"><span data-stu-id="60019-148">No</span></span>|  
|<span data-ttu-id="60019-149">Windows Hizmeti</span><span class="sxs-lookup"><span data-stu-id="60019-149">Windows Service</span></span>|<span data-ttu-id="60019-150">Hayır</span><span class="sxs-lookup"><span data-stu-id="60019-150">No</span></span>|  
|<span data-ttu-id="60019-151">Web Sitesi</span><span class="sxs-lookup"><span data-stu-id="60019-151">Web Site</span></span>|<span data-ttu-id="60019-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="60019-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60019-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60019-153">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="60019-154">Nesneler</span><span class="sxs-lookup"><span data-stu-id="60019-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="60019-155">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="60019-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="60019-156">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="60019-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="60019-157">Uygulama Formlarına Erişme</span><span class="sxs-lookup"><span data-stu-id="60019-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
