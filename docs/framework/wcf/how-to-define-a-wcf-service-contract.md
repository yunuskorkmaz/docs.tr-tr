---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlama'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: ba88fc6ba4cba8d46ed1b43080d471b1b7c4bd75
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928881"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="694ff-102">Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlama</span><span class="sxs-lookup"><span data-stu-id="694ff-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="694ff-103">Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevden ilki açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="694ff-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="694ff-104">Öğreticilere genel bakış için bkz [. Öğretici: Windows Communication Foundation uygulamaları](getting-started-tutorial.md)ile çalışmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="694ff-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="694ff-105">Bir WCF hizmeti oluşturduğunuzda, ilk göreviniz bir hizmet sözleşmesini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="694ff-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="694ff-106">Hizmet sözleşmesi, hizmetin desteklediği işlemleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="694ff-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="694ff-107">Bir işlem, bir Web hizmeti yöntemi olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="694ff-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="694ff-108">Bir görsel C# veya VISUAL BASIC (vb) arabirimi tanımlayarak hizmet sözleşmeleri oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="694ff-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="694ff-109">Bir arabirim aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="694ff-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="694ff-110">Arabirimdeki her yöntem belirli bir hizmet işlemine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="694ff-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="694ff-111">Her arabirim için <xref:System.ServiceModel.ServiceContractAttribute> özniteliği uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="694ff-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="694ff-112">Her işlem/yöntem için <xref:System.ServiceModel.OperationContractAttribute> özniteliği uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="694ff-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="694ff-113">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="694ff-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="694ff-114">Bir **WCF hizmet kitaplığı** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="694ff-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="694ff-115">Bir hizmet sözleşmesi arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="694ff-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="694ff-116">Bir WCF hizmet kitaplığı projesi oluşturma ve bir hizmet sözleşmesi arabirimi tanımlama</span><span class="sxs-lookup"><span data-stu-id="694ff-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="694ff-117">Visual Studio 'Yu yönetici olarak açın.</span><span class="sxs-lookup"><span data-stu-id="694ff-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="694ff-118">Bunu yapmak için **Başlat** menüsünde Visual Studio programını seçin ve ardından kısayol menüsünde**yönetici olarak çalıştır** ' **ı seçin.**  > </span><span class="sxs-lookup"><span data-stu-id="694ff-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="694ff-119">Bir **WCF hizmet kitaplığı** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="694ff-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="694ff-120">Gelen **dosya** menüsünde **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="694ff-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="694ff-121">**Yeni proje** iletişim kutusunda, sol tarafta,  **C# Visual** veya **Visual Basic**' i genişletin ve ardından **WCF** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="694ff-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="694ff-122">Visual Studio, pencerenin orta bölümündeki proje şablonlarının bir listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="694ff-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="694ff-123">**WCF hizmet kitaplığı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="694ff-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="694ff-124">**WCF** proje şablonu kategorisini görmüyorsanız, Visual Studio 'nun **Windows Communication Foundation** bileşenini yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="694ff-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="694ff-125">**Yeni proje** iletişim kutusunda, sol taraftaki **Visual Studio yükleyicisi aç** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="694ff-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="694ff-126">**Ayrı bileşenler** sekmesini seçin ve ardından **geliştirme etkinlikleri** kategorisinin **Windows Communication Foundation** bulun ve seçin.</span><span class="sxs-lookup"><span data-stu-id="694ff-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="694ff-127">Bileşeni yüklemeye başlamak için **Değiştir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="694ff-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="694ff-128">Pencerenin alt bölümünde, **ad** Için *GettingStartedLib* ve **çözüm adı**olarak *gettingstarted* girin.</span><span class="sxs-lookup"><span data-stu-id="694ff-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="694ff-129">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="694ff-129">Select **OK**.</span></span>

      <span data-ttu-id="694ff-130">Visual Studio, üç dosya içeren projeyi oluşturur: Bir Visual Basic projesi için *IService1.cs* (veya *IService1. vb* ), *Service1.cs* (veya *Service1. Visual Basic vb* ) ve *app. config*. Visual Studio bu dosyaları aşağıdaki gibi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="694ff-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="694ff-131">*IService1* dosyası, hizmet sözleşmesinin varsayılan tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="694ff-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="694ff-132">*Service1* dosyası, hizmet sözleşmesinin varsayılan uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="694ff-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="694ff-133">*App. config* dosyası, VISUAL Studio WCF hizmeti ana bilgisayar aracı ile varsayılan hizmeti yüklemek için gereken yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="694ff-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="694ff-134">WCF hizmeti ana bilgisayar aracı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="694ff-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="694ff-135">Visual Studio 'Yu Visual Basic Geliştirici ortamı ayarları ile yüklediyseniz, çözüm gizlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="694ff-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="694ff-136">Bu durumda, **Araçlar** menüsünden **Seçenekler** ' i seçin ve ardından **Seçenekler** penceresinde **Projeler ve çözümler** > **genel** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="694ff-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="694ff-137">**Çözümü her zaman göster**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="694ff-137">Select **Always show solution**.</span></span> <span data-ttu-id="694ff-138">Ayrıca, **oluşturulduğunda yeni projeleri kaydet** ' in seçili olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="694ff-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="694ff-139">**Çözüm Gezgini**, **IService1.cs** veya **IService1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="694ff-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="694ff-140">Bu sözleşme, çevrimiçi bir Hesaplayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="694ff-140">This contract defines an online calculator.</span></span> <span data-ttu-id="694ff-141">Arabirimin özniteliğiyle (Basitleştirilmiş olarak `ServiceContract`) işaretlendiğini görürsünüz. <xref:System.ServiceModel.ServiceContractAttribute> `ICalculator`</span><span class="sxs-lookup"><span data-stu-id="694ff-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="694ff-142">Bu öznitelik, anlaşma adının belirsizliğini ortadan kaldırmak için bir ad alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="694ff-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="694ff-143">Kod, her Hesaplayıcı işlemini <xref:System.ServiceModel.OperationContractAttribute> özniteliğiyle (Basitleştirilmiş olarak `OperationContract`) işaretler.</span><span class="sxs-lookup"><span data-stu-id="694ff-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="694ff-144">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="694ff-144">Next steps</span></span>

<span data-ttu-id="694ff-145">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="694ff-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="694ff-146">Bir WCF hizmet kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="694ff-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="694ff-147">Bir hizmet sözleşmesi arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="694ff-147">Define a service contract interface.</span></span>

<span data-ttu-id="694ff-148">WCF hizmeti sözleşmesinin nasıl uygulanacağını öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="694ff-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="694ff-149">Öğretici: WCF hizmet sözleşmesi uygulama</span><span class="sxs-lookup"><span data-stu-id="694ff-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
