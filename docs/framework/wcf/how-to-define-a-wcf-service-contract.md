---
title: 'Öğretici: Bir Windows Communication Foundation Hizmet sözleşmesini tanımlama'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: a1908339460191fcb81d03d45c56dd57b2cf4c4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929356"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="2a55d-102">Öğretici: Bir Windows Communication Foundation Hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="2a55d-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="2a55d-103">Bu öğretici, ilk beş görev temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken açıklar.</span><span class="sxs-lookup"><span data-stu-id="2a55d-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="2a55d-104">Öğreticiler genel bakış için bkz. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="2a55d-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="2a55d-105">Bir WCF Hizmeti oluşturduğunuzda, ilk göreviniz bir hizmet sözleşmesini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2a55d-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="2a55d-106">Hizmet sözleşmesi hangi işlemleri belirtir destekler.</span><span class="sxs-lookup"><span data-stu-id="2a55d-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="2a55d-107">Bir işlem, bir Web hizmeti yöntemi düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="2a55d-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="2a55d-108">Hizmet sözleşmeleri görsel tanımlayarak oluşturduğunuz C# veya Visual Basic (VB) arabirim.</span><span class="sxs-lookup"><span data-stu-id="2a55d-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="2a55d-109">Bir arabirim, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2a55d-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="2a55d-110">Arabirimdeki her yöntem için bir hizmet işlemiyle karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="2a55d-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="2a55d-111">Her arabirim için uygulamanız gerekir <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2a55d-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="2a55d-112">Her işlem/yöntem için uygulamalısınız <xref:System.ServiceModel.OperationContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2a55d-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="2a55d-113">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="2a55d-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="2a55d-114">Oluşturma bir **WCF hizmet Kitaplığı** proje.</span><span class="sxs-lookup"><span data-stu-id="2a55d-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="2a55d-115">Bir hizmet sözleşme arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2a55d-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="2a55d-116">Bir WCF hizmet kitaplığı projesi oluşturun ve hizmet sözleşme arabirimi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="2a55d-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="2a55d-117">Visual Studio'yu yönetici olarak açın.</span><span class="sxs-lookup"><span data-stu-id="2a55d-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="2a55d-118">Bunu yapmak için Visual Studio programda seçin **Başlat** menüsüne ve ardından **daha fazla** > **yönetici olarak çalıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="2a55d-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="2a55d-119">Oluşturma bir **WCF hizmet Kitaplığı** proje.</span><span class="sxs-lookup"><span data-stu-id="2a55d-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="2a55d-120">Gelen **dosya** menüsünde **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="2a55d-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="2a55d-121">İçinde **yeni proje** iletişim kutusunda sol taraftaki genişletin **Visual C#** veya **Visual Basic**ve ardından **WCF** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="2a55d-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="2a55d-122">Visual Studio Proje şablonları listesi penceresinin Merkezi bölümünde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2a55d-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="2a55d-123">Seçin **WCF hizmet Kitaplığı**.</span><span class="sxs-lookup"><span data-stu-id="2a55d-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="2a55d-124">Görmüyorsanız **WCF** proje şablonu kategorisi yüklemeniz gerekebilir **Windows Communication Foundation** Visual Studio bileşen.</span><span class="sxs-lookup"><span data-stu-id="2a55d-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="2a55d-125">İçinde **yeni proje** iletişim kutusunda **açık Visual Studio yükleyicisi** sol tarafındaki bağlantıyı.</span><span class="sxs-lookup"><span data-stu-id="2a55d-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="2a55d-126">Seçin **tek tek bileşenler** sekmesine ve ardından bulmak ve seçmek **Windows Communication Foundation** altında **geliştirme etkinliklerini** kategorisi.</span><span class="sxs-lookup"><span data-stu-id="2a55d-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="2a55d-127">Seçin **Değiştir** bileşeni yüklemeyi başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="2a55d-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="2a55d-128">Pencerenin alt kısmında girin *GettingStartedLib* için **adı** ve *GettingStarted* için **çözüm adı**.</span><span class="sxs-lookup"><span data-stu-id="2a55d-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="2a55d-129">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="2a55d-129">Select **OK**.</span></span>

      <span data-ttu-id="2a55d-130">Visual Studio üç dosyayı içeren projenin oluşturur: *Iservice1.cs* (veya *Iservice1.vb* Visual Basic projesi için), *Service1.cs* (veya *Service1.vb* Visual Basic projesi için), ve  *App.config*. Visual Studio, bu dosyalar gibi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="2a55d-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="2a55d-131">*Iservice1* dosyası varsayılan hizmet sözleşmesi tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="2a55d-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="2a55d-132">*Service1* varsayılan uygulama hizmet sözleşmesinin dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="2a55d-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="2a55d-133">*App.config* dosyası Visual Studio WCF hizmet konağı aracıyla varsayılan hizmetini yüklemek için gereken yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2a55d-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="2a55d-134">WCF hizmet konağı aracı hakkında daha fazla bilgi için bkz. [WCF hizmet Konağı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2a55d-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="2a55d-135">Visual Basic Geliştirici ortam ayarları ile Visual Studio yüklü değilse, çözüm gizlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a55d-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="2a55d-136">Bu durumda, seçin **seçenekleri** gelen **Araçları** menüsü, ardından **projeler ve çözümler** > **genel** içinde **seçenekleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="2a55d-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="2a55d-137">Seçin **çözümü her zaman göster**.</span><span class="sxs-lookup"><span data-stu-id="2a55d-137">Select **Always show solution**.</span></span> <span data-ttu-id="2a55d-138">Ayrıca, doğrulayın **oluşturulduğunda yeni projeleri Kaydet** seçilir.</span><span class="sxs-lookup"><span data-stu-id="2a55d-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="2a55d-139">Gelen **Çözüm Gezgini**açın **Iservice1.cs** veya **Iservice1.vb** dosya ve kendi kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="2a55d-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="2a55d-140">Bu sözleşme, çevrimiçi bir hesap makinesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2a55d-140">This contract defines an online calculator.</span></span> <span data-ttu-id="2a55d-141">Bildirim `ICalculator` arabirimi ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği (olarak Basitleştirilmiş `ServiceContract`).</span><span class="sxs-lookup"><span data-stu-id="2a55d-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="2a55d-142">Bu öznitelik sözleşme adı ayırt etmek için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2a55d-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="2a55d-143">Her hesap makinesi işlemle kodu işaretler <xref:System.ServiceModel.OperationContractAttribute> özniteliği (olarak Basitleştirilmiş `OperationContract`).</span><span class="sxs-lookup"><span data-stu-id="2a55d-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2a55d-144">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2a55d-144">Next steps</span></span>

<span data-ttu-id="2a55d-145">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="2a55d-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="2a55d-146">Bir WCF hizmet kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a55d-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="2a55d-147">Bir hizmet sözleşme arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2a55d-147">Define a service contract interface.</span></span>

<span data-ttu-id="2a55d-148">WCF hizmet sözleşmesini uygulama konusunda bilgi almak için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="2a55d-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a55d-149">Öğretici: Bir WCF Hizmeti sözleşmesi uygulama</span><span class="sxs-lookup"><span data-stu-id="2a55d-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
