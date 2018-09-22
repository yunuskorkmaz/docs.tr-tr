---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Tanımlama'
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 4f85a51c47eb045d1d2f0111cb217199c9acf0d7
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537884"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="d5e90-102">Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d5e90-102">How to: Define a Windows Communication Foundation Service Contract</span></span>

<span data-ttu-id="d5e90-103">İlk altı görev temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur.</span><span class="sxs-lookup"><span data-stu-id="d5e90-103">This is the first of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="d5e90-104">Tüm altı görevleri genel bakış için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d5e90-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

 <span data-ttu-id="d5e90-105">Bir WCF Hizmeti oluştururken, ilk görev bir hizmet sözleşmesini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="d5e90-105">When creating a WCF service, the first task is to define a service contract.</span></span> <span data-ttu-id="d5e90-106">Hizmet sözleşmesi hangi işlemleri belirtir destekler.</span><span class="sxs-lookup"><span data-stu-id="d5e90-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="d5e90-107">Bir işlem, bir Web hizmeti yöntemi düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="d5e90-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="d5e90-108">Sözleşmeler, bir C++, C# veya Visual Basic (VB) arabirimi tanımlamasıyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d5e90-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="d5e90-109">Arabirimdeki her yöntem için bir hizmet işlemiyle karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d5e90-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="d5e90-110">Her arabirimde <xref:System.ServiceModel.ServiceContractAttribute> uygulanan ve her bir işlem olmalıdır <xref:System.ServiceModel.OperationContractAttribute> özniteliğinin.</span><span class="sxs-lookup"><span data-stu-id="d5e90-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="d5e90-111">Arabirimdeki bir yöntem mümkünse <xref:System.ServiceModel.ServiceContractAttribute> özniteliği yok <xref:System.ServiceModel.OperationContractAttribute> öznitelik, hizmet tarafından yöntemi gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="d5e90-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>

 <span data-ttu-id="d5e90-112">Bu görev için kullanılan kod, aşağıdaki yordamın örnekte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d5e90-112">The code used for this task is provided in the example following the procedure.</span></span>

## <a name="define-a-service-contract"></a><span data-ttu-id="d5e90-113">Bir hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="d5e90-113">Define a service contract</span></span>

1. <span data-ttu-id="d5e90-114">Visual Studio'yu yönetici olarak açın programa sağ tıklayarak **Başlat** menü ve seçerek **daha fazla** > **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="d5e90-114">Open Visual Studio as an administrator by right-clicking the program in the **Start** menu and selecting **More** > **Run as administrator**.</span></span>

2. <span data-ttu-id="d5e90-115">Bir WCF hizmet kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5e90-115">Create a WCF Service Library project.</span></span>

   1. <span data-ttu-id="d5e90-116">Gelen **dosya** menüsünde **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="d5e90-116">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="d5e90-117">İçinde **yeni proje** iletişim kutusunda sol taraftaki genişletin **Visual C#** veya **Visual Basic**ve ardından **WCF** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="d5e90-117">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="d5e90-118">Proje şablonları listesi, iletişim kutusunun merkez bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d5e90-118">A list of project templates is displayed in the center section of the dialog.</span></span> <span data-ttu-id="d5e90-119">Seçin **WCF hizmet Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="d5e90-119">Select **WCF Service Library**.</span></span>

   3. <span data-ttu-id="d5e90-120">Girin `GettingStartedLib` içinde **adı** metin kutusu ve `GettingStarted` içinde **çözüm adı** iletişim kutusunun altındaki metin.</span><span class="sxs-lookup"><span data-stu-id="d5e90-120">Enter `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d5e90-121">Görmüyorsanız **WCF** proje şablonu kategorisi yüklemeniz gerekebilir **Windows Communication Foundation** Visual Studio bileşen.</span><span class="sxs-lookup"><span data-stu-id="d5e90-121">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="d5e90-122">İçinde **yeni proje** iletişim kutusunda, bağlantısına **açık Visual Studio yükleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="d5e90-122">In the **New Project** dialog box, click the link that says **Open Visual Studio Installer**.</span></span> <span data-ttu-id="d5e90-123">Seçin **tek tek bileşenler** sekmesine ve ardından bulmak ve seçmek **Windows Communication Foundation** altında **geliştirme etkinliklerini** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="d5e90-123">Select the **Individual Components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="d5e90-124">Seçin **Değiştir** bileşeni yüklemeyi başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="d5e90-124">Choose **Modify** to begin installing the component.</span></span>

   <span data-ttu-id="d5e90-125">Visual Studio 3 dosyaları içeren projeyi oluşturur: Iservice1.cs (veya Iservice1.vb) Service1.cs (veya gt;service1.vb) ve App.config. Varsayılan hizmet sözleşmesini Iservice1 dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="d5e90-125">Visual Studio creates the project, which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config. The IService1 file contains a default service contract.</span></span> <span data-ttu-id="d5e90-126">Varsayılan bir uygulama hizmet sözleşmesinin Service1 dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="d5e90-126">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="d5e90-127">App.config dosyasını Visual Studio WCF hizmet konağı varsayılan hizmetiyle yüklemek için gerekli yapılandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="d5e90-127">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="d5e90-128">WCF hizmet konağı aracı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="d5e90-128">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>

3. <span data-ttu-id="d5e90-129">Iservice1.cs veya Iservice1.vb dosyasını açın ve ad alanı bildirimi bırakarak ad alanı bildirimi içindeki kod silin.</span><span class="sxs-lookup"><span data-stu-id="d5e90-129">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration, leaving the namespace declaration.</span></span> <span data-ttu-id="d5e90-130">Ad alanı içinde bildirimi adlı yeni arabirimi tanımlayın `ICalculator` aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d5e90-130">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     <span data-ttu-id="d5e90-131">Bu sözleşme, çevrimiçi bir hesap makinesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5e90-131">This contract defines an online calculator.</span></span> <span data-ttu-id="d5e90-132">Bildirim `ICalculator` arabirimi ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d5e90-132">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="d5e90-133">Bu öznitelik sözleşme adı ayırt etmek için kullanılan bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5e90-133">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="d5e90-134">Her hesap makinesi işlemi ile işaretlenmiş <xref:System.ServiceModel.OperationContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d5e90-134">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d5e90-135">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d5e90-135">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d5e90-136">Nasıl yapılır: bir hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="d5e90-136">How to: Implement a service contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a><span data-ttu-id="d5e90-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5e90-137">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="d5e90-138">Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama</span><span class="sxs-lookup"><span data-stu-id="d5e90-138">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="d5e90-139">Başlarken</span><span class="sxs-lookup"><span data-stu-id="d5e90-139">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="d5e90-140">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="d5e90-140">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)