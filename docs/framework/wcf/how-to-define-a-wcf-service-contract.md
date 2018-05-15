---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Tanımlama'
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5e8abbf8c5f9b0696d90ccbee94c5d8f4dd8b1ec
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="fd803-102">Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="fd803-102">How to: Define a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="fd803-103">Temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken altı görevler ilk budur.</span><span class="sxs-lookup"><span data-stu-id="fd803-103">This is the first of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="fd803-104">Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="fd803-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="fd803-105">Bir WCF Hizmeti oluştururken, ilk görevi bir hizmet sözleşmesini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="fd803-105">When creating a WCF service, the first task is to define a service contract.</span></span> <span data-ttu-id="fd803-106">Hizmet sözleşmesi hangi işlemleri belirtir hizmet destekler.</span><span class="sxs-lookup"><span data-stu-id="fd803-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="fd803-107">Bir işlem, bir Web hizmeti yöntemi düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="fd803-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="fd803-108">Sözleşmeler, C++, C# veya Visual Basic (VB) arabirimi tanımlamasıyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fd803-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="fd803-109">Arabirimdeki her yöntem belirli hizmet işlemine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="fd803-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="fd803-110">Her arabirimde <xref:System.ServiceModel.ServiceContractAttribute> uygulanan ve her işlem olmalıdır <xref:System.ServiceModel.OperationContractAttribute> özniteliğinin.</span><span class="sxs-lookup"><span data-stu-id="fd803-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="fd803-111">Bir yöntemi varsa içeren bir arabirim içinde <xref:System.ServiceModel.ServiceContractAttribute> özniteliği yok <xref:System.ServiceModel.OperationContractAttribute> özniteliği yöntemi hizmeti tarafından gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="fd803-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>  
  
 <span data-ttu-id="fd803-112">Bu görev için kullanılan kod, aşağıdaki yordamın örnekte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fd803-112">The code used for this task is provided in the example following the procedure.</span></span>  
  
### <a name="to-define-a-service-contract"></a><span data-ttu-id="fd803-113">Bir hizmet sözleşmesini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="fd803-113">To define a service contract</span></span>  
  
1.  <span data-ttu-id="fd803-114">Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] programa sağ tarafından yönetici olarak **Başlat** menü ve seçerek **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="fd803-114">Open  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] as an administrator by right-clicking the program in the **Start** menu and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="fd803-115">Tıklayarak bir WCF Hizmeti kitaplığı projesi oluşturma **dosya** menü ve seçerek **yeni**, **proje**.</span><span class="sxs-lookup"><span data-stu-id="fd803-115">Create a WCF Service Library project by clicking the **File** menu and selecting **New**, **Project**.</span></span> <span data-ttu-id="fd803-116">İçinde **yeni proje** iletişim kutusunda, iletişim kutusunun sol tarafında genişletin **Visual C#** bir C# projesi için veya **diğer diller** ve ardından **Visual Basic** Visual Basic projesinde için.</span><span class="sxs-lookup"><span data-stu-id="fd803-116">In the **New Project** dialog, on the left-hand side of the dialog expand **Visual C#** for a C# project or **Other Languages** and then **Visual Basic** for a Visual Basic project.</span></span> <span data-ttu-id="fd803-117">Seçili dili altında seçin **WCF** ve proje şablonları listesini iletişim merkezi bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fd803-117">Under the language selected select **WCF** and a list of project templates will be displayed on the center section of the dialog.</span></span> <span data-ttu-id="fd803-118">Seçin **WCF Hizmeti Kitaplığı**ve türü `GettingStartedLib` içinde **adı** textbox ve `GettingStarted` içinde **çözüm adı** iletişim kutusunun altındaki metin kutusuna.</span><span class="sxs-lookup"><span data-stu-id="fd803-118">Select **WCF Service Library**, and type `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>  
  
3.  <span data-ttu-id="fd803-119">Visual Studio 3 dosyaları içeren proje oluşturma: IService1.cs (veya IService1.vb) service1.cs dosyasını (veya Service1.vb) ve App.config.  Varsayılan hizmet sözleşmesini IService1 dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="fd803-119">Visual Studio will create the project which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config.  The IService1 file contains a default service contract.</span></span>  <span data-ttu-id="fd803-120">Service1 dosyayı varsayılan uygulama hizmet sözleşmesinin içerir.</span><span class="sxs-lookup"><span data-stu-id="fd803-120">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="fd803-121">App.config dosyasını Visual Studio WCF hizmet konağı varsayılan hizmetiyle yüklemek için gerekli yapılandırmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="fd803-121">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="fd803-122">WCF hizmet konağı aracı hakkında daha fazla bilgi için bkz: [WCF hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="fd803-122">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>  
  
4.  <span data-ttu-id="fd803-123">IService1.cs veya IService1.vb dosyasını açın ve ad alanı bildirimi bırakarak ad alanı bildiriminin içindeki kod silin.</span><span class="sxs-lookup"><span data-stu-id="fd803-123">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration leaving the namespace declaration.</span></span> <span data-ttu-id="fd803-124">İçinde ad alanı bildirimi tanımlamak adlı yeni bir arabirim `ICalculator` aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fd803-124">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
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
  
    ```  
    ‘IService.vb  
    Imports System  
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
  
     <span data-ttu-id="fd803-125">Bu sözleşme çevrimiçi hesaplayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fd803-125">This contract defines an online calculator.</span></span> <span data-ttu-id="fd803-126">Bildirim `ICalculator` arabirimi ile işaretlenmiş <xref:System.ServiceModel.ServiceContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fd803-126">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="fd803-127">Bu öznitelik sözleşme adı ayırt etmek için kullanılan bir ad alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fd803-127">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="fd803-128">Her hesap makinesi işlemi ile işaretlenmiş <xref:System.ServiceModel.OperationContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fd803-128">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fd803-129">Bir arabirim, üye veya sınıf ek açıklama eklemek için öznitelikleri kullanma, öznitelik adı "Özniteliği" bölümü düşürebilir.</span><span class="sxs-lookup"><span data-stu-id="fd803-129">When using attributes to annotate an interface, member, or class, you can drop the "Attribute" part from the attribute name.</span></span> <span data-ttu-id="fd803-130">Bu nedenle <xref:System.ServiceModel.ServiceContractAttribute> hale `[ServiceContract]` C# veya `<ServiceContract>` Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="fd803-130">So <xref:System.ServiceModel.ServiceContractAttribute> becomes `[ServiceContract]` in C#, or `<ServiceContract>` in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd803-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd803-131">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="fd803-132">Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama</span><span class="sxs-lookup"><span data-stu-id="fd803-132">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="fd803-133">Başlarken</span><span class="sxs-lookup"><span data-stu-id="fd803-133">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="fd803-134">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="fd803-134">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
