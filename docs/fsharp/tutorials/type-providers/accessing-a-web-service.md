---
title: "İzlenecek yol - tür sağlayıcıları (F #) kullanarak Web hizmetine erişim"
description: "Web Hizmetleri Açıklama Dili (WSDL) türü sağlayıcısı F # 3.0 kullanılabilir bir WSDL hizmete erişmek için nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 2929198172a4e9f908daa64af19208e07859263f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a><span data-ttu-id="ff584-104">İzlenecek yol: Tür Sağlayıcılarını Kullanarak Web Hizmetine Erişim</span><span class="sxs-lookup"><span data-stu-id="ff584-104">Walkthrough: Accessing a Web Service by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="ff584-105">Bu kılavuz, F # 3.0 için yazılmıştır ve güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ff584-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="ff584-106">Bkz: [FSharp.Data](https://fsharp.github.io/FSharp.Data/) güncel, platformlar arası tür sağlayıcıları için.</span><span class="sxs-lookup"><span data-stu-id="ff584-106">See [FSharp.Data](https://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="ff584-107">API başvuru bağlantılar için MSDN götürür.</span><span class="sxs-lookup"><span data-stu-id="ff584-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="ff584-108">Docs.microsoft.com API Başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="ff584-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="ff584-109">Bu kılavuz, F # bir WSDL hizmete erişmek için 3. 0'kullanılabilir Web Hizmetleri Açıklama Dili (WSDL) türü sağlayıcısının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff584-109">This walkthrough shows you how to use the Web Services Description Language (WSDL) type provider that is available in F# 3.0 to access a WSDL service.</span></span> <span data-ttu-id="ff584-110">Diğer .NET dilleri tarafından arama svcutil.exe web hizmetine erişmek için kod oluşturmak veya web başvuru ekleyerek, örneğin, C# proje sizin için svcutil.exe çağırmak için Visual Studio almak için.</span><span class="sxs-lookup"><span data-stu-id="ff584-110">In other .NET languages, you generate the code to access the web service by calling svcutil.exe, or by adding a web reference in, for example, a C# project to get Visual Studio to call svcutil.exe for you.</span></span> <span data-ttu-id="ff584-111">F #'ta, WsdlService tür oluşturan kodu yazma WSDL türü sağlayıcısı kadar kısa sürede, kullanarak ek bir seçeneğiniz vardır, türleri oluşturulur ve kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="ff584-111">In F#, you have the additional option of using the WSDL type provider, so as soon as you write the code that creates the WsdlService type, the types are generated and become available.</span></span> <span data-ttu-id="ff584-112">Bu işlem kodu yazarken kullanılabilir olmasını durduracak Hizmeti'ne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ff584-112">This process relies on the service being available when you are writing the code.</span></span>

<span data-ttu-id="ff584-113">Bu kılavuz aşağıdaki görevler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ff584-113">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="ff584-114">Bu sırada başarılı olması gözden geçirme tamamlamalısınız:</span><span class="sxs-lookup"><span data-stu-id="ff584-114">You must complete them in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="ff584-115">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff584-115">Creating the project</span></span>
<br />

- <span data-ttu-id="ff584-116">Tür sağlayıcısını yapılandırma </span><span class="sxs-lookup"><span data-stu-id="ff584-116">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="ff584-117">Web hizmeti çağıran ve sonuçları işleme</span><span class="sxs-lookup"><span data-stu-id="ff584-117">Calling the web service, and processing the results</span></span>
<br />


## <a name="creating-the-project"></a><span data-ttu-id="ff584-118">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff584-118">Creating the project</span></span>
<span data-ttu-id="ff584-119">Adımda bir proje oluşturun ve WSDL tür sağlayıcısı kullanmak için uygun başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ff584-119">In the step, you create a project and add the appropriate references to use a WSDL type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="ff584-120">Bir F# projesi oluşturmak ve ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ff584-120">To create and set up an F# project</span></span>

1. <span data-ttu-id="ff584-121">Yeni bir F # konsol uygulama projesi açın.</span><span class="sxs-lookup"><span data-stu-id="ff584-121">Open a new F# Console Application project.</span></span>
<br />

2. <span data-ttu-id="ff584-122">İçinde **Çözüm Gezgini**, projenin için kısayol menüsünü açın **başvuru** düğümünü ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="ff584-122">In **Solution Explorer**, open the shortcut menu for the project's **Reference** node, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="ff584-123">İçinde **derlemeleri** alanı seçin **Framework**ve ardından kullanılabilir derlemeleri listesinden seçip **System.Runtime.Serialization** ve  **System.ServiceModel**.</span><span class="sxs-lookup"><span data-stu-id="ff584-123">In the **Assemblies** area, choose **Framework**, and then, in the list of available assemblies, choose **System.Runtime.Serialization** and **System.ServiceModel**.</span></span>
<br />

4. <span data-ttu-id="ff584-124">İçinde **derlemeleri** alanı seçin **uzantıları**.</span><span class="sxs-lookup"><span data-stu-id="ff584-124">In the **Assemblies** area, choose **Extensions**.</span></span>
<br />

5. <span data-ttu-id="ff584-125">Kullanılabilir derlemeleri listesinden seçip **FSharp.Data.TypeProviders**ve ardından **Tamam** düğmesi bu derlemelerine başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ff584-125">In the list of available assemblies, choose **FSharp.Data.TypeProviders**, and then choose the **OK** button to add references to these assemblies.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="ff584-126">Tür sağlayıcısını yapılandırma </span><span class="sxs-lookup"><span data-stu-id="ff584-126">Configuring the type provider</span></span>
<span data-ttu-id="ff584-127">Bu adımda, TerraServer web hizmeti türleri oluşturmak için WSDL türü sağlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff584-127">In this step, you use the WSDL type provider to generate types for the TerraServer web service.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="ff584-128">Tür sağlayıcısını yapılandırmak ve türleri üretmek için</span><span class="sxs-lookup"><span data-stu-id="ff584-128">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="ff584-129">Aşağıdaki türü sağlayıcı ad alanı açmak için kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ff584-129">Add the following line of code to open the type provider namespace.</span></span>
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. <span data-ttu-id="ff584-130">Aşağıdaki web hizmetiyle türü sağlayıcısı çağırmak için kod satırını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ff584-130">Add the following line of code to invoke the type provider with a web service.</span></span> <span data-ttu-id="ff584-131">Bu örnekte, TerraServer web hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff584-131">In this example, use the TerraServer web service.</span></span>
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "https://terraserver-usa.com/TerraService2.asmx?WSDL" https://msrmaps.com/TerraService2.asmx?WSDL">
```

  <span data-ttu-id="ff584-132">Kırmızı dalgalı hizmet URI'si yanlış yazılmış olup olmadığını hizmeti çalışmıyor veya gerçekleştirme değil, bu kod satırı altında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ff584-132">A red squiggle appears under this line of code if the service URI is misspelled or if the service itself is down or isn’t performing.</span></span> <span data-ttu-id="ff584-133">Kod noktası ise, bir hata iletisi sorununu açıklar.</span><span class="sxs-lookup"><span data-stu-id="ff584-133">If you point to the code, an error message describes the problem.</span></span> <span data-ttu-id="ff584-134">Aynı bilgiler bulabilirsiniz **hata listesi** penceresi veya **çıktı penceresi** oluşturacağınız sonra.</span><span class="sxs-lookup"><span data-stu-id="ff584-134">You can find the same information in the **Error List** window or in the **Output Window** after you build.</span></span>
<br />  <span data-ttu-id="ff584-135">Proje için app.config dosyasını kullanarak veya statik tür parametreleri tür sağlayıcı bildiriminde kullanarak bir WSDL bağlantısı için yapılandırma ayarlarını belirtmek için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="ff584-135">There are two ways to specify configuration settings for a WSDL connection, by using the app.config file for the project, or by using the static type parameters in the type provider declaration.</span></span> <span data-ttu-id="ff584-136">Uygun yapılandırma dosyası öğelerini oluşturmak için svcutil.exe kullanma.</span><span class="sxs-lookup"><span data-stu-id="ff584-136">You can use svcutil.exe to generate appropriate configuration file elements.</span></span> <span data-ttu-id="ff584-137">Bir web hizmeti için yapılandırma bilgilerini oluşturmak için svcutil.exe kullanma hakkında daha fazla bilgi için bkz: [ServiceModel meta veri yardımcı Programracı &#40; Svcutil.exe &#41; ](https://msdn.microsoft.com/library/aa347733.aspx).</span><span class="sxs-lookup"><span data-stu-id="ff584-137">For more information about using svcutil.exe to generate configuration information for a web service, see [ServiceModel Metadata Utility Tool &#40;Svcutil.exe&#41;](https://msdn.microsoft.com/library/aa347733.aspx).</span></span> <span data-ttu-id="ff584-138">Statik tür parametreleri WSDL türü sağlayıcısı için tam bir açıklaması için bkz: [WsdlService türü sağlayıcısı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="ff584-138">For a full description of the static type parameters for the WSDL type provider, see [WsdlService Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span></span>
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a><span data-ttu-id="ff584-139">Web hizmeti çağıran ve sonuçları işleme</span><span class="sxs-lookup"><span data-stu-id="ff584-139">Calling the web service, and processing the results</span></span>
<span data-ttu-id="ff584-140">Her web hizmeti parametreleri olarak kendi yöntem çağrıları için kullanılan türleri kendi kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="ff584-140">Each web service has its own set of types that are used as parameters for its method calls.</span></span> <span data-ttu-id="ff584-141">Bu adımda, bu parametreler hazırlamak, bir web yöntemini çağırın ve bu bilgileri işlem.</span><span class="sxs-lookup"><span data-stu-id="ff584-141">In this step, you prepare these parameters, call a web method, and process the information that it returns.</span></span>


#### <a name="to-call-the-web-service-and-process-the-results"></a><span data-ttu-id="ff584-142">Web hizmetini çağırmak ve sonuçları işlemek için</span><span class="sxs-lookup"><span data-stu-id="ff584-142">To call the web service, and process the results</span></span>

1. <span data-ttu-id="ff584-143">Web hizmeti zaman aşımına uğrar veya web hizmeti çağrısı bir özel durum işleme bloğu içinde içermelidir şekilde, çalışmamaya olabilir.</span><span class="sxs-lookup"><span data-stu-id="ff584-143">The web service might time out or stop functioning, so you should include the web service call in an exception handling block.</span></span> <span data-ttu-id="ff584-144">Web hizmetinden veri al denemek için aşağıdaki kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="ff584-144">Write the following code to try to get data from the web service.</span></span>
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

<span data-ttu-id="ff584-145">Gibi web hizmeti için gerekli olan veri türleri oluşturmak fark **yer** ve **konumu**, iç içe geçmiş türler WsdlService altında yazarken **TerraService**.</span><span class="sxs-lookup"><span data-stu-id="ff584-145">Notice that you create the data types that are needed for the web service, such as **Place** and **Location**, as nested types under the WsdlService type **TerraService**.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="ff584-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff584-146">See Also</span></span>
[<span data-ttu-id="ff584-147">WsdlService türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="ff584-147">WsdlService Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[<span data-ttu-id="ff584-148">Tür Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="ff584-148">Type Providers</span></span>](index.md)
