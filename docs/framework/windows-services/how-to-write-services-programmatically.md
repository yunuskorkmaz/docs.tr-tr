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
ms.openlocfilehash: 29e0b95ad91c93f3a23246daf2be128b10d7e2ce
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952403"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="8d4c1-102">Nasıl yapılır: Hizmetleri Program Aracılığıyla Yazma</span><span class="sxs-lookup"><span data-stu-id="8d4c1-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="8d4c1-103">Windows hizmeti proje şablonunu kullanmayı tercih ederseniz, devralma ve diğer altyapı öğelerini kendiniz ayarlayarak kendi hizmetlerinizi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="8d4c1-104">Programlı olarak bir hizmet oluşturduğunuzda, şablonun sizin için başka bir tanıtıcı tutacağından birkaç adım gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8d4c1-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="8d4c1-105"><xref:System.ServiceProcess.ServiceBase> Sınıfından devralması için hizmet sınıfınızı ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="8d4c1-106">Hizmet projeniz için çalıştırılacak `Main` hizmetleri tanımlayan bir yöntem oluşturmanız ve üzerinde <xref:System.ServiceProcess.ServiceBase.Run%2A> yöntemi çağırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="8d4c1-107"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Ve<xref:System.ServiceProcess.ServiceBase.OnStop%2A> yordamlarını geçersiz kılmanız ve çalıştırmak istediğiniz kodu doldurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="8d4c1-108">Program aracılığıyla bir hizmet yazmak için</span><span class="sxs-lookup"><span data-stu-id="8d4c1-108">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="8d4c1-109">Boş bir proje oluşturun ve aşağıdaki adımları izleyerek gerekli ad alanlarına bir başvuru oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8d4c1-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="8d4c1-110">**Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="8d4c1-111">**.NET Framework** sekmesinde **System. dll** ' ye kaydırın ve **Seç**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="8d4c1-112">**System. ServiceProcess. dll** ' ye kaydırın ve **Seç**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="8d4c1-113">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-113">Click **OK**.</span></span>  
  
2. <span data-ttu-id="8d4c1-114">Bir sınıf ekleyin ve bunu öğesinden <xref:System.ServiceProcess.ServiceBase>devralacak şekilde yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="8d4c1-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="8d4c1-115">Hizmet sınıfınızı yapılandırmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8d4c1-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="8d4c1-116">Sınıfınız için `Main` bir yöntem oluşturun ve sınıfınızın içereceği hizmeti tanımlamak için kullanın; `userService1` , sınıfının adıdır:</span><span class="sxs-lookup"><span data-stu-id="8d4c1-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="8d4c1-117"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Yöntemini geçersiz kılın ve hizmetiniz başlatıldığında gerçekleşmesini istediğiniz işlemleri tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="8d4c1-118">İçin özel işlem tanımlamak istediğiniz diğer yöntemleri geçersiz kılın ve hizmetin her durumda gerçekleşmesi gereken eylemleri belirlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="8d4c1-119">Hizmet uygulamanız için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="8d4c1-120">Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanıza](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="8d4c1-121">**Build** menüsünden **Build Solution** ' i seçerek projenizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8d4c1-122">Projenizi çalıştırmak için F5 tuşuna basmayın; bir hizmet projesini bu şekilde çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="8d4c1-123">Hizmetinizi yüklemek için bir kurulum projesi ve özel eylemler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="8d4c1-124">Bir örnek için bkz [. İzlenecek yol: Bileşen tasarımcısında](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)bir Windows hizmeti uygulaması oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="8d4c1-125">Hizmetini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-125">Install the service.</span></span> <span data-ttu-id="8d4c1-126">Daha fazla bilgi için [nasıl yapılır: Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)yükleme ve kaldırma.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4c1-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d4c1-127">See also</span></span>

- [<span data-ttu-id="8d4c1-128">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="8d4c1-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="8d4c1-129">Nasıl yapılır: Windows Hizmetleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d4c1-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="8d4c1-130">Nasıl yapılır: Hizmet uygulamanıza yükleyiciler ekleme</span><span class="sxs-lookup"><span data-stu-id="8d4c1-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="8d4c1-131">Nasıl yapılır: Hizmetlerle Ilgili bilgileri günlüğe kaydet</span><span class="sxs-lookup"><span data-stu-id="8d4c1-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [<span data-ttu-id="8d4c1-132">İzlenecek yol: Bileşen tasarımcısında bir Windows hizmeti uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d4c1-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
