---
title: 'Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: f0affeabba90e1d4cdc559cb96dee2dafe0bea77
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073994"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="e7cca-102">Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma</span><span class="sxs-lookup"><span data-stu-id="e7cca-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="e7cca-103">Windows hizmet proje şablonu kullanmayı tercih ederseniz, devralma ve diğer altyapı öğelerini kendiniz ayarlama hizmetlerinizi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7cca-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="e7cca-104">Program aracılığıyla bir hizmet oluşturduğunuzda, şablon, aksi takdirde gerçekleştirilir birkaç adım gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="e7cca-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
-   <span data-ttu-id="e7cca-105">Hizmet sınıfınızı devralınacak ayarlamalısınız <xref:System.ServiceProcess.ServiceBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e7cca-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
-   <span data-ttu-id="e7cca-106">Oluşturmalısınız bir `Main` yöntemi çağırır ve çalıştırmak için hizmeti tanımlayan bir hizmet projesi için <xref:System.ServiceProcess.ServiceBase.Run%2A> bunları yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e7cca-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
-   <span data-ttu-id="e7cca-107">Geçersiz kılmanız gerekir <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamlar ve herhangi bir kod girin, istediğiniz çalışmak üzere.</span><span class="sxs-lookup"><span data-stu-id="e7cca-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="e7cca-108">Bir hizmet programlı olarak yazmak için</span><span class="sxs-lookup"><span data-stu-id="e7cca-108">To write a service programmatically</span></span>  
  
1.  <span data-ttu-id="e7cca-109">Boş bir proje oluşturun ve aşağıdaki adımları izleyerek ad alanlarına başvuru oluşturun:</span><span class="sxs-lookup"><span data-stu-id="e7cca-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1.  <span data-ttu-id="e7cca-110">İçinde **Çözüm Gezgini**, sağ **başvuruları** düğüm ve tıklatın **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e7cca-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="e7cca-111">Üzerinde **.NET Framework** sekmesinde, kaydırma **System.dll** tıklatıp **seçin**.</span><span class="sxs-lookup"><span data-stu-id="e7cca-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3.  <span data-ttu-id="e7cca-112">Kaydırma **System.ServiceProcess.dll** tıklatıp **seçin**.</span><span class="sxs-lookup"><span data-stu-id="e7cca-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4.  <span data-ttu-id="e7cca-113">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="e7cca-113">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="e7cca-114">Bir sınıf ekleyin ve devralınacak şekilde yapılandırmanız <xref:System.ServiceProcess.ServiceBase>:</span><span class="sxs-lookup"><span data-stu-id="e7cca-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  <span data-ttu-id="e7cca-115">Hizmet sınıfınızı yapılandırmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e7cca-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  <span data-ttu-id="e7cca-116">Oluşturma bir `Main` sınıfınız için bir yöntem ve sınıfınızın içerir; hizmet tanımlamak için kullanın `userService1` sınıf adıdır:</span><span class="sxs-lookup"><span data-stu-id="e7cca-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  <span data-ttu-id="e7cca-117">Geçersiz kılma <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi ve hizmetinizi başlatıldığında gerçekleşmesini istediğiniz herhangi bir işlemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e7cca-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  <span data-ttu-id="e7cca-118">Özel işlemeyi tanımlamak istediğiniz diğer yöntemleri geçersiz kılın ve hizmetinin her durumda gerçekleştirmesi gereken eylemleri belirlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="e7cca-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7.  <span data-ttu-id="e7cca-119">Hizmet uygulamanız için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e7cca-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="e7cca-120">Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamasına yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="e7cca-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8.  <span data-ttu-id="e7cca-121">Projenizi seçerek **Çözümü Derle** gelen **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="e7cca-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7cca-122">Projenizi çalıştırmak için F5 tuşuna basmayın-bu şekilde bir hizmet projesi çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="e7cca-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="e7cca-123">Bir kurulum projesi ve hizmetinizi yüklemek için özel eylemler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e7cca-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="e7cca-124">Bir örnek için bkz [izlenecek yol: Oluşturma bir Windows hizmet uygulaması Bileşen Tasarımcısı'nda](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e7cca-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="e7cca-125">Hizmetini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e7cca-125">Install the service.</span></span> <span data-ttu-id="e7cca-126">Daha fazla bilgi için [nasıl yapılır: Hizmetleri Yükleme ve kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="e7cca-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7cca-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7cca-127">See also</span></span>

- [<span data-ttu-id="e7cca-128">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="e7cca-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="e7cca-129">Nasıl yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7cca-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="e7cca-130">Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="e7cca-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="e7cca-131">Nasıl yapılır: Hizmet Bilgilerini Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="e7cca-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [<span data-ttu-id="e7cca-132">İzlenecek yol: Bileşen tasarımcısında Windows hizmeti uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7cca-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
