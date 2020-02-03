---
title: BindingSource kullanarak bir Web hizmetine bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
ms.openlocfilehash: 0680c73e578577cf40158761f6c635fe30ff9f4d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746674"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="98e6e-102">Nasıl yapılır: Windows Forms BindingSource ile Bir Web Hizmetine Bağlama</span><span class="sxs-lookup"><span data-stu-id="98e6e-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="98e6e-103">Bir Windows form denetimini bir XML Web hizmeti çağırma işleminden elde edilen sonuçlara bağlamak istiyorsanız, bir <xref:System.Windows.Forms.BindingSource> bileşeni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98e6e-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="98e6e-104">Bu yordam <xref:System.Windows.Forms.BindingSource> bileşeni bir türe bağlamaya benzer.</span><span class="sxs-lookup"><span data-stu-id="98e6e-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="98e6e-105">Web hizmeti tarafından sunulan yöntemleri ve türleri içeren bir istemci tarafı proxy oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="98e6e-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="98e6e-106">Web hizmeti (. asmx) içinden veya Web Hizmetleri Açıklama Dili (WSDL) dosyasından bir istemci tarafı ara sunucu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98e6e-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="98e6e-107">Ayrıca, istemci tarafı proxy 'niz Web hizmeti tarafından kullanılan karmaşık türlerin alanlarını genel özellikler olarak kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98e6e-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="98e6e-108">Ardından <xref:System.Windows.Forms.BindingSource> Web hizmeti proxy 'sinde gösterilen türlerden birine bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="98e6e-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="98e6e-109">İstemci tarafı ara sunucusu oluşturmak ve bu sunucuya bağlamak için</span><span class="sxs-lookup"><span data-stu-id="98e6e-109">To create and bind to a client-side proxy</span></span>  
  
1. <span data-ttu-id="98e6e-110">Tercih ettiğiniz dizinde uygun bir ad alanı ile bir Windows formu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="98e6e-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2. <span data-ttu-id="98e6e-111">Forma bir <xref:System.Windows.Forms.BindingSource> bileşeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="98e6e-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3. <span data-ttu-id="98e6e-112">Windows yazılım geliştirme seti (SDK) komut istemi ' ni açın ve formunuzun bulunduğu dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="98e6e-112">Open the Windows Software Development Kit (SDK) command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4. <span data-ttu-id="98e6e-113">WSDL aracını kullanarak Web hizmeti için. asmx veya WSDL dosyasının URL 'sini, ardından uygulamanızın ad alanını ve isteğe bağlı olarak çalıştığınız dili `wsdl` girin.</span><span class="sxs-lookup"><span data-stu-id="98e6e-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="98e6e-114">Aşağıdaki kod örneği `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`konumunda bulunan Web hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="98e6e-114">The following code example uses the Web service located at `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span></span> <span data-ttu-id="98e6e-115">Örneğin, tür `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`C# için veya `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`Visual Basic türü için.</span><span class="sxs-lookup"><span data-stu-id="98e6e-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="98e6e-116">Yolu WSDL aracına bir bağımsız değişken olarak geçirmek, uygulamanız ile aynı dizin ve ad alanında belirtilen dilde bir istemci tarafı ara sunucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98e6e-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="98e6e-117">Visual Studio kullanıyorsanız, dosyayı projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="98e6e-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5. <span data-ttu-id="98e6e-118">Bağlanacak istemci tarafı proxy 'sinde bir tür seçin.</span><span class="sxs-lookup"><span data-stu-id="98e6e-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="98e6e-119">Bu genellikle Web hizmeti tarafından sunulan bir yöntem tarafından döndürülen türdür.</span><span class="sxs-lookup"><span data-stu-id="98e6e-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="98e6e-120">Seçilen türdeki alanlar bağlama amaçları için ortak özellikler olarak kullanıma sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98e6e-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. <span data-ttu-id="98e6e-121"><xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğini, Web hizmeti istemci tarafı proxy 'sinde yer alan istediğiniz türe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="98e6e-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="98e6e-122">Denetimleri bir Web hizmetine bağlı BindingSource 'a bağlamak için</span><span class="sxs-lookup"><span data-stu-id="98e6e-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
- <span data-ttu-id="98e6e-123">Bir parametre olarak istediğiniz Web hizmeti türünün genel özelliğini geçirerek <xref:System.Windows.Forms.BindingSource>denetimleri bağlayın.</span><span class="sxs-lookup"><span data-stu-id="98e6e-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="98e6e-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="98e6e-124">Example</span></span>  
 <span data-ttu-id="98e6e-125">Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.BindingSource> bileşenini Web hizmetine bağlamayı ve sonra bir metin kutusunu <xref:System.Windows.Forms.BindingSource> bileşenine bağlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="98e6e-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="98e6e-126">Düğmeye tıkladığınızda, bir Web hizmeti yöntemi çağırılır ve sonuçlar `textbox1`görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="98e6e-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98e6e-127">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="98e6e-127">Compiling the Code</span></span>  
 <span data-ttu-id="98e6e-128">Bu, bir `Main` yöntemi ve istemci tarafı proxy kodunun kısaltılmış bir sürümünü içeren tam bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="98e6e-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="98e6e-129">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="98e6e-129">This example requires:</span></span>  
  
- <span data-ttu-id="98e6e-130">System, System. Drawing, System. Web. Services, System. Windows. Forms ve System. xml derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="98e6e-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e6e-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98e6e-131">See also</span></span>

- [<span data-ttu-id="98e6e-132">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="98e6e-132">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="98e6e-133">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="98e6e-133">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
