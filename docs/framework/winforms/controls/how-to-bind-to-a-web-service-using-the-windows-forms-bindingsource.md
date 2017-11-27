---
title: "Nasıl yapılır: Windows Forms BindingSource ile Bir Web Hizmetine Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5024ad9000811aa438183de240c91b659644a7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="2d316-102">Nasıl yapılır: Windows Forms BindingSource ile Bir Web Hizmetine Bağlama</span><span class="sxs-lookup"><span data-stu-id="2d316-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="2d316-103">XML Web hizmeti çağırma sonucu elde edilen sonuçlar Windows Form denetimi bağlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2d316-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="2d316-104">Bu yordam bağlama benzer bir <xref:System.Windows.Forms.BindingSource> türü için bileşen.</span><span class="sxs-lookup"><span data-stu-id="2d316-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="2d316-105">Web hizmeti tarafından sunulan türleri ve yöntemleri içeren bir istemci-tarafı proxy oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2d316-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="2d316-106">Bir istemci-tarafı proxy Web hizmetinden (.asmx) kendisi ya da Web Hizmetleri Açıklama Dili (WSDL) dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2d316-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="2d316-107">Ayrıca, istemci-tarafı proxy, ortak özellik olarak Web hizmeti tarafından kullanılan karmaşık türler alanları açığa gerekir.</span><span class="sxs-lookup"><span data-stu-id="2d316-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="2d316-108">Ardından bağlamak <xref:System.Windows.Forms.BindingSource> Web üzerinde açığa türlerinden birini proxy hizmet.</span><span class="sxs-lookup"><span data-stu-id="2d316-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="2d316-109">Oluşturma ve bir istemci-tarafı proxy bağlamak için</span><span class="sxs-lookup"><span data-stu-id="2d316-109">To create and bind to a client-side proxy</span></span>  
  
1.  <span data-ttu-id="2d316-110">Uygun bir ad alanı ile tercih ettiğiniz dizininde bir Windows Form oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2d316-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2.  <span data-ttu-id="2d316-111">Ekleme bir <xref:System.Windows.Forms.BindingSource> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="2d316-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3.  <span data-ttu-id="2d316-112">Açık [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] komut istemi ve formunuza bulunan aynı dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="2d316-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4.  <span data-ttu-id="2d316-113">WSDL aracını kullanarak girin `wsdl` .asmx veya WSDL dosyası Web hizmeti URL'sini ve ardından uygulamanızı ad alanı tarafından ve isteğe bağlı olarak dil çalıştığınız.</span><span class="sxs-lookup"><span data-stu-id="2d316-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="2d316-114">Aşağıdaki kod örneğinde http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx bulunan Web hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2d316-114">The following code example uses the Web service located at http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx.</span></span> <span data-ttu-id="2d316-115">Örneğin, C# türü `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, veya Visual Basic türü `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span><span class="sxs-lookup"><span data-stu-id="2d316-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="2d316-116">Yolun WSDL için bağımsız değişken olarak geçirme aracı bir istemci-tarafı proxy aynı dizin ve ad alanı, uygulamanızda belirtilen dil olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2d316-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="2d316-117">Kullanıyorsanız [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], dosyayı projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2d316-117">If you are using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], add the file to your project.</span></span>  
  
5.  <span data-ttu-id="2d316-118">Bağlamak için istemci tarafı proxy bir tür seçin.</span><span class="sxs-lookup"><span data-stu-id="2d316-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="2d316-119">Bu genellikle Web hizmeti tarafından önerilen bir yöntem tarafından döndürülen bir türü olur.</span><span class="sxs-lookup"><span data-stu-id="2d316-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="2d316-120">Seçilen türünde alanlar bağlama amacıyla için genel özellikleri olarak sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d316-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  <span data-ttu-id="2d316-121">Ayarlama <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği <xref:System.Windows.Forms.BindingSource> istediğiniz diğer bir deyişle türünü bulunan Web hizmeti istemci-tarafı proxy'si.</span><span class="sxs-lookup"><span data-stu-id="2d316-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="2d316-122">Bir Web hizmetine bağlı BindingSource denetimleri bağlamak için</span><span class="sxs-lookup"><span data-stu-id="2d316-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
-   <span data-ttu-id="2d316-123">Denetimlere bağlama <xref:System.Windows.Forms.BindingSource>, istediğiniz Web Hizmet türüne ilişkin ortak özelliği parametre olarak geçirme.</span><span class="sxs-lookup"><span data-stu-id="2d316-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="2d316-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d316-124">Example</span></span>  
 <span data-ttu-id="2d316-125">Aşağıdaki kod örneğinde nasıl bağlanacağını gösterir bir <xref:System.Windows.Forms.BindingSource> bir Web hizmeti bileşeni ve bir metin kutusunu bağlamak nasıl <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="2d316-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="2d316-126">Düğmesini tıklatın, bir Web hizmeti yöntemi olarak adlandırılır ve sonuçları görünür `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="2d316-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d316-127">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2d316-127">Compiling the Code</span></span>  
 <span data-ttu-id="2d316-128">Bu içeren, tam bir örnektir bir `Main` yöntemi ve istemci tarafı proxy kodu kısaltılmış bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="2d316-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="2d316-129">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2d316-129">This example requires:</span></span>  
  
-   <span data-ttu-id="2d316-130">Sistem, System.Drawing, System.Web.Services, System.Windows.Forms ve System.Xml derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="2d316-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="2d316-131">Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2d316-131">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2d316-132">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="2d316-132">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="2d316-133">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="2d316-133">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d316-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d316-134">See Also</span></span>  
 [<span data-ttu-id="2d316-135">BindingSource bileşeni</span><span class="sxs-lookup"><span data-stu-id="2d316-135">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="2d316-136">Nasıl yapılır: Windows Forms denetimini bir türe bağlama</span><span class="sxs-lookup"><span data-stu-id="2d316-136">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
