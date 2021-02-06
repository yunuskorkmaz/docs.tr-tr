---
description: ': My. WebServices nesnesi hakkında daha fazla bilgi edinin'
title: My.WebServices Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: e8d7ef8b349fef6d69b92d9df4a23222bd3c912e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640543"
---
# <a name="mywebservices-object"></a><span data-ttu-id="b973b-103">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="b973b-103">My.WebServices Object</span></span>

<span data-ttu-id="b973b-104">Geçerli proje tarafından başvurulan her bir XML Web hizmetinin tek bir örneğini oluşturmaya ve bunlara erişmeye yönelik özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b973b-104">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b973b-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b973b-105">Remarks</span></span>  

 <span data-ttu-id="b973b-106">`My.WebServices`Nesnesi, geçerli proje tarafından başvurulan her bir Web hizmetinin örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b973b-106">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="b973b-107">Her örnek isteğe bağlı olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b973b-107">Each instance is instantiated on demand.</span></span> <span data-ttu-id="b973b-108">Bu Web hizmetlerine nesnenin özellikleri aracılığıyla erişebilirsiniz `My.WebServices` .</span><span class="sxs-lookup"><span data-stu-id="b973b-108">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="b973b-109">Özelliğin adı, özelliğin eriştiği Web hizmetinin adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b973b-109">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="b973b-110">Öğesinden devralan tüm sınıflar <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> bir Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="b973b-110">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="b973b-111">Bir projeye Web Hizmetleri ekleme hakkında daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="b973b-111">For information about adding Web services to a project, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="b973b-112">`My.WebServices`Nesne yalnızca geçerli projeyle Ilişkili Web hizmetlerini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="b973b-112">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="b973b-113">Başvurulan DLL 'lerde belirtilen Web hizmetlerine erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b973b-113">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="b973b-114">Bir DLL 'nin sağladığı bir Web hizmetine erişmek için, Web hizmeti 'nin adı *dlladı* biçiminde kullanmanız gerekir. *WebServiceName*.</span><span class="sxs-lookup"><span data-stu-id="b973b-114">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="b973b-115">Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="b973b-115">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="b973b-116">Nesne ve özellikleri Web uygulamaları için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b973b-116">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b973b-117">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b973b-117">Properties</span></span>  

 <span data-ttu-id="b973b-118">Nesnesinin her özelliği, `My.WebServices` geçerli proje tarafından başvurulan bir Web hizmeti örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b973b-118">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="b973b-119">Özelliğin adı, özelliğin eriştiği Web hizmeti adı ile aynıdır ve özellik türü, Web hizmetinin türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b973b-119">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b973b-120">Ad çakışması varsa, bir Web hizmetine erişmek için özellik adı *RootNamespace* _ *ad* alanı \_ *HizmetAdı* olur.</span><span class="sxs-lookup"><span data-stu-id="b973b-120">If there is a name collision, the property name for accessing a Web service is *RootNamespace* _ *Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="b973b-121">Örneğin, adlı iki Web hizmeti göz önünde bulundurun `Service1` .</span><span class="sxs-lookup"><span data-stu-id="b973b-121">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="b973b-122">Bu hizmetlerden biri kök ad alanında ve ad alanında ise `WindowsApplication1` `Namespace1` , kullanarak bu hizmete erişirsiniz `My.WebServices.WindowsApplication1_Namespace1_Service1` .</span><span class="sxs-lookup"><span data-stu-id="b973b-122">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="b973b-123">Nesnenin özelliklerinden birine ilk kez eriştiğinizde `My.WebServices` , Web hizmetinin yeni bir örneğini oluşturur ve depolar.</span><span class="sxs-lookup"><span data-stu-id="b973b-123">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="b973b-124">Bu özelliğin sonraki erişimleri, Web hizmetinin bu örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b973b-124">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="b973b-125">`Nothing`Bu Web hizmeti için özelliğine atayarak bir Web hizmetini atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b973b-125">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="b973b-126">Özellik ayarlayıcısı `Nothing` saklı değere atar.</span><span class="sxs-lookup"><span data-stu-id="b973b-126">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="b973b-127">Özelliği dışında bir değer atarsanız `Nothing` , ayarlayıcı bir <xref:System.ArgumentException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b973b-127">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="b973b-128">Bir `My.WebServices` nesnenin özelliğinin, veya işlecini kullanarak bir Web hizmeti örneğini depolayıp depomadığını test edebilirsiniz `Is` `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="b973b-128">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="b973b-129">Özelliğin değerinin olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="b973b-129">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b973b-130">Genellikle, `Is` veya `IsNot` işlecinin karşılaştırmayı gerçekleştirmek için özelliğinin değerini okuması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b973b-130">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="b973b-131">Ancak, özelliği şu anda depoluyorsa `Nothing` , özelliği Web hizmetinin yeni bir örneğini oluşturur ve ardından bu örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="b973b-131">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="b973b-132">Ancak, Visual Basic Derleyicisi `My.WebServices` nesnenin özelliklerini özel olarak değerlendirir ve `Is` veya `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b973b-132">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b973b-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="b973b-133">Example</span></span>  

 <span data-ttu-id="b973b-134">Bu örnek, `FahrenheitToCelsius` `TemperatureConverter` XML Web hizmetinin yöntemini çağırır ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b973b-134">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 <span data-ttu-id="b973b-135">Bu örneğin çalışması için, projeniz adlı bir Web hizmetine başvurmalıdır `Converter` ve Web hizmeti yöntemi kullanıma sunmalıdır `ConvertTemperature` .</span><span class="sxs-lookup"><span data-stu-id="b973b-135">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="b973b-136">Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="b973b-136">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="b973b-137">Bu kod, bir Web uygulaması projesinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b973b-137">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b973b-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b973b-138">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="b973b-139">Proje Türüne Göre Kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="b973b-139">Availability by Project Type</span></span>  
  
|<span data-ttu-id="b973b-140">Proje türü</span><span class="sxs-lookup"><span data-stu-id="b973b-140">Project type</span></span>|<span data-ttu-id="b973b-141">Kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="b973b-141">Available</span></span>|  
|---|---|  
|<span data-ttu-id="b973b-142">Windows uygulaması</span><span class="sxs-lookup"><span data-stu-id="b973b-142">Windows Application</span></span>|<span data-ttu-id="b973b-143">**Evet**</span><span class="sxs-lookup"><span data-stu-id="b973b-143">**Yes**</span></span>|  
|<span data-ttu-id="b973b-144">Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b973b-144">Class Library</span></span>|<span data-ttu-id="b973b-145">**Evet**</span><span class="sxs-lookup"><span data-stu-id="b973b-145">**Yes**</span></span>|  
|<span data-ttu-id="b973b-146">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="b973b-146">Console Application</span></span>|<span data-ttu-id="b973b-147">**Evet**</span><span class="sxs-lookup"><span data-stu-id="b973b-147">**Yes**</span></span>|  
|<span data-ttu-id="b973b-148">Windows Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b973b-148">Windows Control Library</span></span>|<span data-ttu-id="b973b-149">**Evet**</span><span class="sxs-lookup"><span data-stu-id="b973b-149">**Yes**</span></span>|  
|<span data-ttu-id="b973b-150">Web Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b973b-150">Web Control Library</span></span>|<span data-ttu-id="b973b-151">**Evet**</span><span class="sxs-lookup"><span data-stu-id="b973b-151">**Yes**</span></span>|  
|<span data-ttu-id="b973b-152">Windows Hizmeti</span><span class="sxs-lookup"><span data-stu-id="b973b-152">Windows Service</span></span>|<span data-ttu-id="b973b-153">**Evet**</span><span class="sxs-lookup"><span data-stu-id="b973b-153">**Yes**</span></span>|  
|<span data-ttu-id="b973b-154">Web Sitesi</span><span class="sxs-lookup"><span data-stu-id="b973b-154">Web Site</span></span>|<span data-ttu-id="b973b-155">No</span><span class="sxs-lookup"><span data-stu-id="b973b-155">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b973b-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b973b-156">See also</span></span>

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [<span data-ttu-id="b973b-157">Uygulama Web Hizmetlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="b973b-157">Accessing Application Web Services</span></span>](../../developing-apps/programming/accessing-application-web-services.md)
