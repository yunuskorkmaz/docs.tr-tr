---
title: 'Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma'
description: Devralma ve diğer altyapı öğelerini kendiniz ayarlayarak bkz. Hizmetleri programlama yoluyla yazma.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
ms.openlocfilehash: cd749d325bec6636243dec1905f79abb5e42f04e
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608406"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="63742-103">Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma</span><span class="sxs-lookup"><span data-stu-id="63742-103">How to: Write Services Programmatically</span></span>
<span data-ttu-id="63742-104">Windows hizmeti proje şablonunu kullanmayı tercih ederseniz, devralma ve diğer altyapı öğelerini kendiniz ayarlayarak kendi hizmetlerinizi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63742-104">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="63742-105">Programlı olarak bir hizmet oluşturduğunuzda, şablonun sizin için başka bir tanıtıcı tutacağından birkaç adım gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="63742-105">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="63742-106">Sınıfından devralması için hizmet sınıfınızı ayarlamanız gerekir <xref:System.ServiceProcess.ServiceBase> .</span><span class="sxs-lookup"><span data-stu-id="63742-106">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="63742-107">`Main`Hizmet projeniz için çalıştırılacak hizmetleri tanımlayan bir yöntem oluşturmanız ve <xref:System.ServiceProcess.ServiceBase.Run%2A> üzerinde yöntemi çağırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="63742-107">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="63742-108">Ve yordamlarını geçersiz kılmanız <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> ve çalıştırmak istediğiniz kodu doldurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="63742-108">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="63742-109">Program aracılığıyla bir hizmet yazmak için</span><span class="sxs-lookup"><span data-stu-id="63742-109">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="63742-110">Boş bir proje oluşturun ve aşağıdaki adımları izleyerek gerekli ad alanlarına bir başvuru oluşturun:</span><span class="sxs-lookup"><span data-stu-id="63742-110">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="63742-111">**Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63742-111">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="63742-112">**.NET Framework** sekmesinde, **System.dll** ' ye kaydırın ve **Seç**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63742-112">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="63742-113">**System.ServiceProcess.dll** kaydırın ve **Seç**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63742-113">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="63742-114">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63742-114">Click **OK**.</span></span>  
  
2. <span data-ttu-id="63742-115">Bir sınıf ekleyin ve bunu öğesinden devralacak şekilde yapılandırın <xref:System.ServiceProcess.ServiceBase> :</span><span class="sxs-lookup"><span data-stu-id="63742-115">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="63742-116">Hizmet sınıfınızı yapılandırmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="63742-116">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="63742-117">`Main`Sınıfınız için bir yöntem oluşturun ve sınıfınızın içereceği hizmeti tanımlamak için kullanın; `userService1` sınıfın adıdır:</span><span class="sxs-lookup"><span data-stu-id="63742-117">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="63742-118">Yöntemini geçersiz kılın <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve hizmetiniz başlatıldığında gerçekleşmesini istediğiniz işlemleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="63742-118">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="63742-119">İçin özel işlem tanımlamak istediğiniz diğer yöntemleri geçersiz kılın ve hizmetin her durumda gerçekleşmesi gereken eylemleri belirlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="63742-119">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="63742-120">Hizmet uygulamanız için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="63742-120">Add the necessary installers for your service application.</span></span> <span data-ttu-id="63742-121">Daha fazla bilgi için bkz. [nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="63742-121">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="63742-122">**Build** menüsünden **Build Solution** ' i seçerek projenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="63742-122">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="63742-123">Projenizi çalıştırmak için F5 tuşuna basmayın; bir hizmet projesini bu şekilde çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="63742-123">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="63742-124">Hizmetinizi yüklemek için bir kurulum projesi ve özel eylemler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="63742-124">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="63742-125">Örnek için bkz. [Izlenecek yol: bileşen tasarımcısında Windows hizmet uygulaması oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="63742-125">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="63742-126">Hizmeti yükler.</span><span class="sxs-lookup"><span data-stu-id="63742-126">Install the service.</span></span> <span data-ttu-id="63742-127">Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="63742-127">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63742-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63742-128">See also</span></span>

- [<span data-ttu-id="63742-129">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="63742-129">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="63742-130">Nasıl yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="63742-130">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="63742-131">Nasıl yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="63742-131">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="63742-132">Nasıl yapılır: Hizmet Bilgilerini Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="63742-132">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="63742-133">İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="63742-133">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
