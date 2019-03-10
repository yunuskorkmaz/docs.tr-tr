---
title: 'Nasıl yapılır: Windows Forms BindingSource ile bir Web hizmetine bağlama'
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
ms.openlocfilehash: 597ffbfb44430379e1ca3709aa88e25fc2f22d46
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722626"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="8199f-102">Nasıl yapılır: Windows Forms BindingSource ile bir Web hizmetine bağlama</span><span class="sxs-lookup"><span data-stu-id="8199f-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="8199f-103">Windows Form denetimi bir XML Web hizmeti çağırma alınan sonuçları bağlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="8199f-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="8199f-104">Bu yordam, bağlama için benzer bir <xref:System.Windows.Forms.BindingSource> bir türü için bileşen.</span><span class="sxs-lookup"><span data-stu-id="8199f-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="8199f-105">Web hizmeti tarafından kullanıma sunulan türleri ve yöntemleri içeren bir istemci-tarafı proxy oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8199f-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="8199f-106">Bir istemci-tarafı proxy Web hizmeti (.asmx) kendisi ya da Web Hizmetleri Açıklama Dili (WSDL) dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8199f-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="8199f-107">Ayrıca, istemci tarafı proxy ortak özellik olarak Web hizmeti tarafından kullanılan karmaşık türler alanları açığa çıkarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8199f-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="8199f-108">Ardından bağlama <xref:System.Windows.Forms.BindingSource> Web kullanıma sunulan türlerden proxy hizmeti.</span><span class="sxs-lookup"><span data-stu-id="8199f-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="8199f-109">Oluşturma ve bir istemci-tarafı proxy sunucuya bağlamak için</span><span class="sxs-lookup"><span data-stu-id="8199f-109">To create and bind to a client-side proxy</span></span>  
  
1.  <span data-ttu-id="8199f-110">Uygun bir ad alanı, seçtiğiniz dizine bir Windows formu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8199f-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2.  <span data-ttu-id="8199f-111">Ekleme bir <xref:System.Windows.Forms.BindingSource> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="8199f-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3.  <span data-ttu-id="8199f-112">Açık [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] komut istemi ve formunuza bulunan aynı dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="8199f-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4.  <span data-ttu-id="8199f-113">WSDL aracını kullanarak girin `wsdl` .asmx veya Web hizmeti için WSDL dosyasının URL'sini uygulamanızı ad alanı tarafından izlenen ve isteğe bağlı olarak dil çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="8199f-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="8199f-114">Aşağıdaki kod örneği konumunda bulunan Web hizmetini kullanır `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span><span class="sxs-lookup"><span data-stu-id="8199f-114">The following code example uses the Web service located at `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span></span> <span data-ttu-id="8199f-115">Örneğin, C# türü için `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, veya Visual Basic türü `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span><span class="sxs-lookup"><span data-stu-id="8199f-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="8199f-116">Yolu için WSDL bağımsız değişken olarak geçirme aracı bir istemci-tarafı proxy aynı dizin ve ad alanı, uygulamanızda belirtilen dil olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8199f-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="8199f-117">Visual Studio kullanıyorsanız, dosyayı projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8199f-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5.  <span data-ttu-id="8199f-118">İstemci tarafı proxy bağlamak için bir tür seçin.</span><span class="sxs-lookup"><span data-stu-id="8199f-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="8199f-119">Web hizmeti tarafından sunulan bir yöntem tarafından döndürülen bir türü genellikle budur.</span><span class="sxs-lookup"><span data-stu-id="8199f-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="8199f-120">Seçilen türündeki alanlar için bağlama amacıyla genel özellikleri olarak sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8199f-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  <span data-ttu-id="8199f-121">Ayarlama <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği <xref:System.Windows.Forms.BindingSource> istediğiniz diğer bir deyişle türe bulunan Web hizmeti taraflı proxy.</span><span class="sxs-lookup"><span data-stu-id="8199f-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="8199f-122">Bir Web hizmetine BindingSource denetimlerini bağlamak için</span><span class="sxs-lookup"><span data-stu-id="8199f-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
-   <span data-ttu-id="8199f-123">Denetimlere bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource>, ortak özelliği, istediğiniz Web hizmet türü bir parametre olarak geçirerek.</span><span class="sxs-lookup"><span data-stu-id="8199f-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="8199f-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="8199f-124">Example</span></span>  
 <span data-ttu-id="8199f-125">Aşağıdaki kod örneğinde nasıl bağlanacağını gösterir. bir <xref:System.Windows.Forms.BindingSource> bir Web hizmeti bileşeni ve bir metin kutusunu bağlamak nasıl <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="8199f-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="8199f-126">Düğmesine tıklayın, bir Web hizmeti yöntemi çağrılır ve sonuçları görünür `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="8199f-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8199f-127">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8199f-127">Compiling the Code</span></span>  
 <span data-ttu-id="8199f-128">Bu içeren tam bir örnek olduğundan bir `Main` yöntemi ve istemci tarafı proxy kodu kısaltılmış sürümü.</span><span class="sxs-lookup"><span data-stu-id="8199f-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="8199f-129">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8199f-129">This example requires:</span></span>  
  
-   <span data-ttu-id="8199f-130">Sistem, System.Drawing System.Web.Services, System.Windows.Forms ve System.Xml derlemesine ilişkin başvurular.</span><span class="sxs-lookup"><span data-stu-id="8199f-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="8199f-131">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8199f-131">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8199f-132">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8199f-132">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8199f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8199f-133">See also</span></span>
- [<span data-ttu-id="8199f-134">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="8199f-134">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="8199f-135">Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="8199f-135">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
