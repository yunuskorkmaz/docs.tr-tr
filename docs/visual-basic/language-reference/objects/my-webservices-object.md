---
title: My.WebServices Nesnesi
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9f2c4017a1df8059f2cc57e7c30a96c474cfda0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="mywebservices-object"></a><span data-ttu-id="7ae08-102">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="7ae08-102">My.WebServices Object</span></span>
<span data-ttu-id="7ae08-103">Oluşturma ve erişme geçerli proje tarafından başvurulan her XML Web hizmetinin tek bir örneği için özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ae08-103">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ae08-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ae08-104">Remarks</span></span>  
 <span data-ttu-id="7ae08-105">`My.WebServices` Nesnesi geçerli proje tarafından başvurulan her Web hizmeti örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ae08-105">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="7ae08-106">İsteğe bağlı olarak her bir örnek örneği.</span><span class="sxs-lookup"><span data-stu-id="7ae08-106">Each instance is instantiated on demand.</span></span> <span data-ttu-id="7ae08-107">Bu Web Hizmetleri özelliklerini erişebilirsiniz `My.WebServices` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7ae08-107">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="7ae08-108">Özelliğin adını özelliğe erişir Web hizmeti adı ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7ae08-108">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="7ae08-109">Öğesinden devralınan herhangi bir sınıf <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> bir Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="7ae08-109">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="7ae08-110">Web Hizmetleri için bir proje ekleme hakkında daha fazla bilgi için bkz: [uygulama Web hizmetlerine erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ae08-110">For information about adding Web services to a project, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="7ae08-111">`My.WebServices` Nesne yalnızca geçerli projeyle ilişkili Web hizmetleri sunar.</span><span class="sxs-lookup"><span data-stu-id="7ae08-111">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="7ae08-112">Başvurulan DLL'lerde bildirilen Web hizmetlerine erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="7ae08-112">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="7ae08-113">DLL sağlayan bir Web hizmetine erişmek için Web hizmeti tam adı biçiminde kullanmalısınız *dll*. *WebServiceName*.</span><span class="sxs-lookup"><span data-stu-id="7ae08-113">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="7ae08-114">Daha fazla bilgi için bkz: [uygulama Web hizmetlerine erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ae08-114">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="7ae08-115">Nesne ve özelliklerini Web uygulamaları için kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="7ae08-115">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7ae08-116">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7ae08-116">Properties</span></span>  
 <span data-ttu-id="7ae08-117">Her bir özelliğinin `My.WebServices` nesne geçerli proje tarafından başvurulan bir Web hizmeti örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ae08-117">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="7ae08-118">Özelliğin adını özelliğe erişir Web hizmeti adı ile aynıdır ve özellik türü Web Service'in türü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7ae08-118">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ae08-119">Bir ad çakışması varsa, Web hizmetine erişim için özellik adı olan *RootNamespace*_*Namespace*\_*ServiceName*.</span><span class="sxs-lookup"><span data-stu-id="7ae08-119">If there is a name collision, the property name for accessing a Web service is *RootNamespace*_*Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="7ae08-120">Örneğin, adında iki Web Hizmetleri göz önünde bulundurun `Service1`.</span><span class="sxs-lookup"><span data-stu-id="7ae08-120">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="7ae08-121">Bu hizmetlerden biri kök ad alanını olup olmadığını `WindowsApplication1` ve ad alanında `Namespace1`, kullanarak bu hizmeti erişir `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span><span class="sxs-lookup"><span data-stu-id="7ae08-121">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="7ae08-122">İlk eriştiğinizde birini `My.WebServices` nesnenin özelliklerini, Web hizmetinin yeni bir örneğini oluşturur ve depolar.</span><span class="sxs-lookup"><span data-stu-id="7ae08-122">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="7ae08-123">Bu özelliğin sonraki erişimleri Web hizmeti örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ae08-123">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="7ae08-124">Bir Web hizmeti atayarak dispose `Nothing` özelliğine bu Web hizmeti.</span><span class="sxs-lookup"><span data-stu-id="7ae08-124">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="7ae08-125">Özellik ayarlayıcısı atar `Nothing` depolanan değer.</span><span class="sxs-lookup"><span data-stu-id="7ae08-125">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="7ae08-126">Herhangi bir değer dışındaki atarsanız `Nothing` özelliğine kurucu oluşturur bir <xref:System.ArgumentException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="7ae08-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="7ae08-127">Bir özelliği olup olmadığını sınayabilirsiniz `My.WebServices` nesnesini kullanarak Web hizmetinin bir örneğini depolar `Is` veya `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="7ae08-127">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="7ae08-128">Özelliğinin değeri olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7ae08-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ae08-129">Genellikle, `Is` veya `IsNot` sahip karşılaştırma yapabilmesi için özellik değeri okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="7ae08-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="7ae08-130">Ancak, özelliği şu anda depoluyorsa `Nothing`, özelliğin Web hizmetini yeni bir örneğini oluşturur ve o örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ae08-130">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="7ae08-131">Ancak, Visual Basic derleyici özelliklerini değerlendirir `My.WebServices` özel nesne ve verir `Is` veya `IsNot` değerini değiştirmeden özelliği durumunu denetlemek için işleci.</span><span class="sxs-lookup"><span data-stu-id="7ae08-131">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ae08-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ae08-132">Example</span></span>  
 <span data-ttu-id="7ae08-133">Bu örnek çağırır `FahrenheitToCelsius` yöntemi `TemperatureConverter` XML Web hizmeti ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ae08-133">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 <span data-ttu-id="7ae08-134">Bu örnek çalışmaya adlı bir Web hizmeti projenizi başvurmalıdır `Converter`, ve bu Web hizmeti kullanıma gerekir `ConvertTemperature` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ae08-134">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="7ae08-135">Daha fazla bilgi için bkz: [uygulama Web hizmetlerine erişme](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ae08-135">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="7ae08-136">Bu kod, bir Web uygulaması projesi çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="7ae08-136">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ae08-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ae08-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="7ae08-138">Proje Türüne Göre Kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="7ae08-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="7ae08-139">Proje türü</span><span class="sxs-lookup"><span data-stu-id="7ae08-139">Project type</span></span>|<span data-ttu-id="7ae08-140">Kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="7ae08-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="7ae08-141">Windows uygulaması</span><span class="sxs-lookup"><span data-stu-id="7ae08-141">Windows Application</span></span>|<span data-ttu-id="7ae08-142">**Evet**</span><span class="sxs-lookup"><span data-stu-id="7ae08-142">**Yes**</span></span>|  
|<span data-ttu-id="7ae08-143">Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="7ae08-143">Class Library</span></span>|<span data-ttu-id="7ae08-144">**Evet**</span><span class="sxs-lookup"><span data-stu-id="7ae08-144">**Yes**</span></span>|  
|<span data-ttu-id="7ae08-145">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="7ae08-145">Console Application</span></span>|<span data-ttu-id="7ae08-146">**Evet**</span><span class="sxs-lookup"><span data-stu-id="7ae08-146">**Yes**</span></span>|  
|<span data-ttu-id="7ae08-147">Windows Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="7ae08-147">Windows Control Library</span></span>|<span data-ttu-id="7ae08-148">**Evet**</span><span class="sxs-lookup"><span data-stu-id="7ae08-148">**Yes**</span></span>|  
|<span data-ttu-id="7ae08-149">Web Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="7ae08-149">Web Control Library</span></span>|<span data-ttu-id="7ae08-150">**Evet**</span><span class="sxs-lookup"><span data-stu-id="7ae08-150">**Yes**</span></span>|  
|<span data-ttu-id="7ae08-151">Windows Hizmeti</span><span class="sxs-lookup"><span data-stu-id="7ae08-151">Windows Service</span></span>|<span data-ttu-id="7ae08-152">**Evet**</span><span class="sxs-lookup"><span data-stu-id="7ae08-152">**Yes**</span></span>|  
|<span data-ttu-id="7ae08-153">Web Sitesi</span><span class="sxs-lookup"><span data-stu-id="7ae08-153">Web Site</span></span>|<span data-ttu-id="7ae08-154">Hayır</span><span class="sxs-lookup"><span data-stu-id="7ae08-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ae08-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ae08-155">See Also</span></span>  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="7ae08-156">Uygulama Web hizmetlerine erişme</span><span class="sxs-lookup"><span data-stu-id="7ae08-156">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
