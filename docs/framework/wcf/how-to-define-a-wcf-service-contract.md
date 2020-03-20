---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlayın'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184086"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="85865-102">Öğretici: Windows Communication Foundation hizmet sözleşmesi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="85865-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="85865-103">Bu öğretici, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevden ilkini açıklar.</span><span class="sxs-lookup"><span data-stu-id="85865-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="85865-104">Öğreticilere genel bir bakış için [Bkz. Öğretici: Windows Communication Foundation uygulamalarıyla başlayın.](getting-started-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="85865-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="85865-105">Bir WCF hizmeti oluşturduğunuzda, ilk göreviniz bir hizmet sözleşmesi tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="85865-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="85865-106">Hizmet sözleşmesi, hizmetin hangi işlemleri desteklediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="85865-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="85865-107">Bir işlem bir Web hizmeti yöntemi olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="85865-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="85865-108">C# veya Visual Basic arabirimi tanımlayarak hizmet sözleşmeleri oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="85865-108">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="85865-109">Arabirim aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="85865-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="85865-110">Arabirimdeki her yöntem belirli bir hizmet işlemine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="85865-110">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="85865-111">Her arabirim için özniteliği uygulamanız <xref:System.ServiceModel.ServiceContractAttribute> gerekir.</span><span class="sxs-lookup"><span data-stu-id="85865-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="85865-112">Her işlem/yöntem için özniteliği <xref:System.ServiceModel.OperationContractAttribute> uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="85865-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="85865-113">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="85865-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="85865-114">Bir **WCF Hizmet Kitaplığı** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85865-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="85865-115">Bir hizmet sözleşmesi arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="85865-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="85865-116">Bir WCF Hizmet Kitaplığı projesi oluşturun ve bir hizmet sözleşmesi arabirimi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="85865-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="85865-117">Yönetici olarak Visual Studio'u açın.</span><span class="sxs-lookup"><span data-stu-id="85865-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="85865-118">Bunu yapmak için **Başlat** menüsünde Visual Studio programını seçin ve ardından kısayol menüsünden yönetici olarak **Daha Fazla** > **Çalıştır'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="85865-119">Bir **WCF Hizmet Kitaplığı** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85865-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="85865-120">**Dosya** menüsünden **Yeni** > **Proje'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="85865-121">Yeni **Proje** iletişim kutusunda, sol tarafta Visual **C#** veya **Visual Basic'i**genişletin ve ardından **WCF** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="85865-122">Visual Studio pencerenin orta bölümünde proje şablonlarının listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="85865-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="85865-123">**WCF Hizmet Kitaplığı'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="85865-124">**WCF** proje şablonu kategorisini görmüyorsanız, Visual Studio'nun **Windows Communication Foundation** bileşenini yüklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="85865-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="85865-125">Yeni **Proje** iletişim kutusunda, sol taraftaki **Görsel Stüdyo Yükleyicisini Aç** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="85865-126">Bireysel **bileşenler** sekmesini seçin ve ardından **Geliştirme etkinlikleri** kategorisi altında Windows **Communication Foundation'ı** bulup seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="85865-127">Bileşeni yüklemeye başlamak için **Değiştir'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="85865-128">Pencerenin alt bölümünde, **Ad** için *BaşlangıçAl'ı* ve **Çözüm adı**için *Başlangıç'ı* girin.</span><span class="sxs-lookup"><span data-stu-id="85865-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="85865-129">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-129">Select **OK**.</span></span>

      <span data-ttu-id="85865-130">Visual Studio üç dosyavardır proje oluşturur: *IService1.cs* (veya *IService1.vb* Visual Basic proje için), *Service1.cs* (veya *Service1.vb* Visual Basic proje için) ve *App.config*. Visual Studio bu dosyaları aşağıdaki gibi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="85865-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="85865-131">*IService1* dosyası, hizmet sözleşmesinin varsayılan tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="85865-131">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="85865-132">*Service1* dosyası, hizmet sözleşmesinin varsayılan uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="85865-132">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="85865-133">*App.config* dosyası Visual Studio WCF Service Host aracı ile varsayılan hizmet yüklemek için gerekli yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="85865-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="85865-134">WCF Service Host aracı hakkında daha fazla bilgi için [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="85865-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="85865-135">Visual Basic geliştirici ortamı ayarlarıyla Visual Studio'yu yüklediyseniz, çözüm gizlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="85865-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="85865-136">Bu durumda, **Araçlar** menüsünden **Seçenekler'i** seçin ve **Ardından Seçenekler** penceresinde Projeler **ve Çözümler** > **Genel'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="85865-137">**Her Zaman çözüm göster'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="85865-137">Select **Always show solution**.</span></span> <span data-ttu-id="85865-138">Ayrıca, **oluşturulduğunda yeni projeleri kaydet** seçildiğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="85865-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="85865-139">**Solution Explorer'dan** **IService1.cs** veya **IService1.vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="85865-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="85865-140">Bu sözleşme bir çevrimiçi hesap makinesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85865-140">This contract defines an online calculator.</span></span> <span data-ttu-id="85865-141">`ICalculator` Arabirimin <xref:System.ServiceModel.ServiceContractAttribute> öznitelik ile işaretlendiğini fark edin (basitleştirilmiş olarak). `ServiceContract`</span><span class="sxs-lookup"><span data-stu-id="85865-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="85865-142">Bu öznitelik, sözleşme adını ayrıştırmak için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85865-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="85865-143">Kod, her hesap makinesi <xref:System.ServiceModel.OperationContractAttribute> işlemini öznitelik `OperationContract`ile işaretler (basitleştirilmiş olarak).</span><span class="sxs-lookup"><span data-stu-id="85865-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="85865-144">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="85865-144">Next steps</span></span>

<span data-ttu-id="85865-145">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="85865-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="85865-146">Bir WCF Hizmet Kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="85865-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="85865-147">Bir hizmet sözleşmesi arabirimi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="85865-147">Define a service contract interface.</span></span>

<span data-ttu-id="85865-148">WCF hizmet sözleşmesini nasıl uygulayacağınızı öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="85865-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="85865-149">Öğretici: WCF hizmet sözleşmesi uygulayın</span><span class="sxs-lookup"><span data-stu-id="85865-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
