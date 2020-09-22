---
title: My.WebServices Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 0b63b44c2cd9d55094fb83fed6c04e4de528a25c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867201"
---
# <a name="mywebservices-object"></a><span data-ttu-id="6edd9-102">My.WebServices Nesnesi</span><span class="sxs-lookup"><span data-stu-id="6edd9-102">My.WebServices Object</span></span>

<span data-ttu-id="6edd9-103">Geçerli proje tarafından başvurulan her bir XML Web hizmetinin tek bir örneğini oluşturmaya ve bunlara erişmeye yönelik özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6edd9-103">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6edd9-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6edd9-104">Remarks</span></span>  

 <span data-ttu-id="6edd9-105">`My.WebServices`Nesnesi, geçerli proje tarafından başvurulan her bir Web hizmetinin örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6edd9-105">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="6edd9-106">Her örnek isteğe bağlı olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6edd9-106">Each instance is instantiated on demand.</span></span> <span data-ttu-id="6edd9-107">Bu Web hizmetlerine nesnenin özellikleri aracılığıyla erişebilirsiniz `My.WebServices` .</span><span class="sxs-lookup"><span data-stu-id="6edd9-107">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="6edd9-108">Özelliğin adı, özelliğin eriştiği Web hizmetinin adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6edd9-108">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="6edd9-109">Öğesinden devralan tüm sınıflar <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> bir Web hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="6edd9-109">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="6edd9-110">Bir projeye Web Hizmetleri ekleme hakkında daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="6edd9-110">For information about adding Web services to a project, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="6edd9-111">`My.WebServices`Nesne yalnızca geçerli projeyle Ilişkili Web hizmetlerini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="6edd9-111">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="6edd9-112">Başvurulan DLL 'lerde belirtilen Web hizmetlerine erişim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="6edd9-112">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="6edd9-113">Bir DLL 'nin sağladığı bir Web hizmetine erişmek için, Web hizmeti 'nin adı *dlladı*biçiminde kullanmanız gerekir. *WebServiceName*.</span><span class="sxs-lookup"><span data-stu-id="6edd9-113">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="6edd9-114">Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="6edd9-114">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="6edd9-115">Nesne ve özellikleri Web uygulamaları için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6edd9-115">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6edd9-116">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6edd9-116">Properties</span></span>  

 <span data-ttu-id="6edd9-117">Nesnesinin her özelliği, `My.WebServices` geçerli proje tarafından başvurulan bir Web hizmeti örneğine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6edd9-117">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="6edd9-118">Özelliğin adı, özelliğin eriştiği Web hizmeti adı ile aynıdır ve özellik türü, Web hizmetinin türüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6edd9-118">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6edd9-119">Ad çakışması varsa, bir Web hizmetine erişmek için özellik adı *RootNamespace*_*ad*alanı \_ *HizmetAdı*olur.</span><span class="sxs-lookup"><span data-stu-id="6edd9-119">If there is a name collision, the property name for accessing a Web service is *RootNamespace*_*Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="6edd9-120">Örneğin, adlı iki Web hizmeti göz önünde bulundurun `Service1` .</span><span class="sxs-lookup"><span data-stu-id="6edd9-120">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="6edd9-121">Bu hizmetlerden biri kök ad alanında ve ad alanında ise `WindowsApplication1` `Namespace1` , kullanarak bu hizmete erişirsiniz `My.WebServices.WindowsApplication1_Namespace1_Service1` .</span><span class="sxs-lookup"><span data-stu-id="6edd9-121">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="6edd9-122">Nesnenin özelliklerinden birine ilk kez eriştiğinizde `My.WebServices` , Web hizmetinin yeni bir örneğini oluşturur ve depolar.</span><span class="sxs-lookup"><span data-stu-id="6edd9-122">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="6edd9-123">Bu özelliğin sonraki erişimleri, Web hizmetinin bu örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6edd9-123">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="6edd9-124">`Nothing`Bu Web hizmeti için özelliğine atayarak bir Web hizmetini atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6edd9-124">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="6edd9-125">Özellik ayarlayıcısı `Nothing` saklı değere atar.</span><span class="sxs-lookup"><span data-stu-id="6edd9-125">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="6edd9-126">Özelliği dışında bir değer atarsanız `Nothing` , ayarlayıcı bir <xref:System.ArgumentException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6edd9-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="6edd9-127">Bir `My.WebServices` nesnenin özelliğinin, veya işlecini kullanarak bir Web hizmeti örneğini depolayıp depomadığını test edebilirsiniz `Is` `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="6edd9-127">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="6edd9-128">Özelliğin değerinin olup olmadığını denetlemek için bu işleçleri kullanabilirsiniz `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="6edd9-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6edd9-129">Genellikle, `Is` veya `IsNot` işlecinin karşılaştırmayı gerçekleştirmek için özelliğinin değerini okuması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6edd9-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="6edd9-130">Ancak, özelliği şu anda depoluyorsa `Nothing` , özelliği Web hizmetinin yeni bir örneğini oluşturur ve ardından bu örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="6edd9-130">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="6edd9-131">Ancak, Visual Basic Derleyicisi `My.WebServices` nesnenin özelliklerini özel olarak değerlendirir ve `Is` veya `IsNot` işlecinin değeri değiştirmeden özelliğin durumunu denetlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6edd9-131">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6edd9-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="6edd9-132">Example</span></span>  

 <span data-ttu-id="6edd9-133">Bu örnek, `FahrenheitToCelsius` `TemperatureConverter` XML Web hizmetinin yöntemini çağırır ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6edd9-133">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 <span data-ttu-id="6edd9-134">Bu örneğin çalışması için, projeniz adlı bir Web hizmetine başvurmalıdır `Converter` ve Web hizmeti yöntemi kullanıma sunmalıdır `ConvertTemperature` .</span><span class="sxs-lookup"><span data-stu-id="6edd9-134">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="6edd9-135">Daha fazla bilgi için bkz. [uygulama Web Hizmetleri 'Ne erişme](../../developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="6edd9-135">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="6edd9-136">Bu kod, bir Web uygulaması projesinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="6edd9-136">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6edd9-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6edd9-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="6edd9-138">Proje Türüne Göre Kullanılabilirlik</span><span class="sxs-lookup"><span data-stu-id="6edd9-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="6edd9-139">Proje türü</span><span class="sxs-lookup"><span data-stu-id="6edd9-139">Project type</span></span>|<span data-ttu-id="6edd9-140">Kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="6edd9-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="6edd9-141">Windows uygulaması</span><span class="sxs-lookup"><span data-stu-id="6edd9-141">Windows Application</span></span>|<span data-ttu-id="6edd9-142">**Evet**</span><span class="sxs-lookup"><span data-stu-id="6edd9-142">**Yes**</span></span>|  
|<span data-ttu-id="6edd9-143">Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6edd9-143">Class Library</span></span>|<span data-ttu-id="6edd9-144">**Evet**</span><span class="sxs-lookup"><span data-stu-id="6edd9-144">**Yes**</span></span>|  
|<span data-ttu-id="6edd9-145">Konsol Uygulaması</span><span class="sxs-lookup"><span data-stu-id="6edd9-145">Console Application</span></span>|<span data-ttu-id="6edd9-146">**Evet**</span><span class="sxs-lookup"><span data-stu-id="6edd9-146">**Yes**</span></span>|  
|<span data-ttu-id="6edd9-147">Windows Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6edd9-147">Windows Control Library</span></span>|<span data-ttu-id="6edd9-148">**Evet**</span><span class="sxs-lookup"><span data-stu-id="6edd9-148">**Yes**</span></span>|  
|<span data-ttu-id="6edd9-149">Web Denetim Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6edd9-149">Web Control Library</span></span>|<span data-ttu-id="6edd9-150">**Evet**</span><span class="sxs-lookup"><span data-stu-id="6edd9-150">**Yes**</span></span>|  
|<span data-ttu-id="6edd9-151">Windows Hizmeti</span><span class="sxs-lookup"><span data-stu-id="6edd9-151">Windows Service</span></span>|<span data-ttu-id="6edd9-152">**Evet**</span><span class="sxs-lookup"><span data-stu-id="6edd9-152">**Yes**</span></span>|  
|<span data-ttu-id="6edd9-153">Web Sitesi</span><span class="sxs-lookup"><span data-stu-id="6edd9-153">Web Site</span></span>|<span data-ttu-id="6edd9-154">Hayır</span><span class="sxs-lookup"><span data-stu-id="6edd9-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6edd9-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6edd9-155">See also</span></span>

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [<span data-ttu-id="6edd9-156">Uygulama Web Hizmetlerine Erişme</span><span class="sxs-lookup"><span data-stu-id="6edd9-156">Accessing Application Web Services</span></span>](../../developing-apps/programming/accessing-application-web-services.md)
