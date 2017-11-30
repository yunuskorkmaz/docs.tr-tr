---
title: My.Forms Nesnesi
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5aa7af1f07a29660335d968c1ecc17be5f8beec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="myforms-object"></a><span data-ttu-id="173f1-102">My.Forms Nesnesi</span><span class="sxs-lookup"><span data-stu-id="173f1-102">My.Forms Object</span></span>
<span data-ttu-id="173f1-103">Geçerli projede bildirilen her Windows formunu örneği erişmek için özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="173f1-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="173f1-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="173f1-104">Remarks</span></span>  
 <span data-ttu-id="173f1-105">`My.Forms` Nesnesi, geçerli projedeki her form örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="173f1-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="173f1-106">Özelliğin adı özelliği erişen formun adı ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="173f1-106">The name of the property is the same as the name of the form that the property accesses.</span></span> <span data-ttu-id="173f1-107">Bir projeye form ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms projeye eklemek](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="173f1-107">For information about adding forms to a project, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="173f1-108">Tarafından sağlanan formların erişebilir `My.Forms` niteliğe olmadan formun adını kullanarak nesne.</span><span class="sxs-lookup"><span data-stu-id="173f1-108">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="173f1-109">Özellik adı formun tür adıyla aynı olduğundan, bu varsayılan bir örnek sahipmiş gibi bir form erişmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="173f1-109">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="173f1-110">Örneğin, `My.Forms.Form1.Show` eşdeğerdir `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="173f1-110">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="173f1-111">`My.Forms` Nesne yalnızca geçerli projeyle ilişkili formları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="173f1-111">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="173f1-112">Başvurulan DLL'lerde bildirilen formlara erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="173f1-112">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="173f1-113">DLL sağlayan form erişmek için tam olarak yazılmış formun adını kullanın *dll*. *Formadı*.</span><span class="sxs-lookup"><span data-stu-id="173f1-113">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="173f1-114">Kullanabileceğiniz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> uygulamanın tüm açık form koleksiyonu alınacağı özellik.</span><span class="sxs-lookup"><span data-stu-id="173f1-114">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="173f1-115">Nesne ve özellikleri yalnızca Windows uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="173f1-115">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="173f1-116">Özellikler</span><span class="sxs-lookup"><span data-stu-id="173f1-116">Properties</span></span>  
 <span data-ttu-id="173f1-117">Her bir özelliğinin `My.Forms` nesne geçerli projedeki form örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="173f1-117">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="173f1-118">Özelliğin adı özelliği erişen formun adı ile aynıdır ve özellik türü formun türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="173f1-118">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="173f1-119">Bir ad çakışması varsa, bir form erişmek için özellik adı olan *RootNamespace*_*Namespace*\_*formadı*.</span><span class="sxs-lookup"><span data-stu-id="173f1-119">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="173f1-120">Örneğin, iki tür adlı göz önünde bulundurun `Form1.`şu biçimlerden birini kök ad alanını olup olmadığını `WindowsApplication1` ve ad alanında `Namespace1`, bu formu üzerinden erişir `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="173f1-120">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="173f1-121">`My.Forms` Nesnesini başlatma sırasında oluşturuldu uygulamanın ana form örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="173f1-121">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="173f1-122">Diğer tüm formların `My.Forms` nesnesi erişilir ve depolar, formun yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="173f1-122">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="173f1-123">Bu özelliğe erişmek için sonraki denemeler formun örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="173f1-123">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="173f1-124">Atayarak biçimi dispose `Nothing` oluşturan özelliğine.</span><span class="sxs-lookup"><span data-stu-id="173f1-124">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="173f1-125">Özellik ayarlayıcı çağrıları <xref:System.Windows.Forms.Form.Close%2A> yöntemi form ve ardından atar `Nothing` depolanan değer.</span><span class="sxs-lookup"><span data-stu-id="173f1-125">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="173f1-126">Herhangi bir değer dışındaki atarsanız `Nothing` özelliğine kurucu oluşturur bir <xref:System.ArgumentException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="173f1-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="173f1-127">Bir özelliği olup olmadığını sınayabilirsiniz `My.Forms` nesnesini kullanarak form örneğini depolar `Is` veya `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="173f1-127">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="173f1-128">Özelliğinin değeri olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="173f1-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="173f1-129">Genellikle, `Is` veya `IsNot` sahip karşılaştırma yapabilmesi için özellik değeri okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="173f1-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="173f1-130">Ancak, özelliği şu anda depoluyorsa `Nothing`, özelliğin formun yeni bir örneğini oluşturur ve o örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="173f1-130">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="173f1-131">Ancak, Visual Basic derleyici özelliklerini değerlendirir `My.Forms` farklı nesne ve verir `Is` veya `IsNot` değerini değiştirmeden özelliği durumunu denetlemek için işleci.</span><span class="sxs-lookup"><span data-stu-id="173f1-131">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="173f1-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="173f1-132">Example</span></span>  
 <span data-ttu-id="173f1-133">Bu örnek varsayılan başlık değiştirir `SidebarMenu` formu.</span><span class="sxs-lookup"><span data-stu-id="173f1-133">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="173f1-134">Çalışmak bu örnek için projenize adlı bir form olmalıdır `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="173f1-134">For this example to work, your project must have a form named `SidebarMenu`.</span></span> <span data-ttu-id="173f1-135">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms projeye eklemek](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="173f1-135">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="173f1-136">Bu kod, yalnızca bir Windows uygulaması proje ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="173f1-136">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="173f1-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="173f1-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="173f1-138">Proje Türüne Göre Kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="173f1-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="173f1-139">Proje türü</span><span class="sxs-lookup"><span data-stu-id="173f1-139">Project type</span></span>|<span data-ttu-id="173f1-140">Kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="173f1-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="173f1-141">Windows uygulaması</span><span class="sxs-lookup"><span data-stu-id="173f1-141">Windows Application</span></span>|<span data-ttu-id="173f1-142">**Evet**</span><span class="sxs-lookup"><span data-stu-id="173f1-142">**Yes**</span></span>|  
|<span data-ttu-id="173f1-143">Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="173f1-143">Class Library</span></span>|<span data-ttu-id="173f1-144">Hayır</span><span class="sxs-lookup"><span data-stu-id="173f1-144">No</span></span>|  
|<span data-ttu-id="173f1-145">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="173f1-145">Console Application</span></span>|<span data-ttu-id="173f1-146">Hayır</span><span class="sxs-lookup"><span data-stu-id="173f1-146">No</span></span>|  
|<span data-ttu-id="173f1-147">Windows Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="173f1-147">Windows Control Library</span></span>|<span data-ttu-id="173f1-148">Hayır</span><span class="sxs-lookup"><span data-stu-id="173f1-148">No</span></span>|  
|<span data-ttu-id="173f1-149">Web Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="173f1-149">Web Control Library</span></span>|<span data-ttu-id="173f1-150">Hayır</span><span class="sxs-lookup"><span data-stu-id="173f1-150">No</span></span>|  
|<span data-ttu-id="173f1-151">Windows Hizmeti</span><span class="sxs-lookup"><span data-stu-id="173f1-151">Windows Service</span></span>|<span data-ttu-id="173f1-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="173f1-152">No</span></span>|  
|<span data-ttu-id="173f1-153">Web Sitesi</span><span class="sxs-lookup"><span data-stu-id="173f1-153">Web Site</span></span>|<span data-ttu-id="173f1-154">Hayır</span><span class="sxs-lookup"><span data-stu-id="173f1-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="173f1-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="173f1-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="173f1-156">Nesneleri</span><span class="sxs-lookup"><span data-stu-id="173f1-156">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="173f1-157">Nasıl yapılır: Windows Forms için bir proje ekleyin</span><span class="sxs-lookup"><span data-stu-id="173f1-157">How to: Add Windows Forms to a Project</span></span>](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)  
 [<span data-ttu-id="173f1-158">Is işleci</span><span class="sxs-lookup"><span data-stu-id="173f1-158">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="173f1-159">IsNot işleci</span><span class="sxs-lookup"><span data-stu-id="173f1-159">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="173f1-160">Uygulama formlarına erişme</span><span class="sxs-lookup"><span data-stu-id="173f1-160">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
