---
title: 'Nasıl Yapılır: Hizmetleri Başlatma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
manager: douge
ms.openlocfilehash: 3c8382d2e425d11dc8aa8b22e361b3cc5637744f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516223"
---
# <a name="how-to-start-services"></a><span data-ttu-id="5ad05-102">Nasıl Yapılır: Hizmetleri Başlatma</span><span class="sxs-lookup"><span data-stu-id="5ad05-102">How to: Start Services</span></span>
<span data-ttu-id="5ad05-103">Bir hizmeti yüklendikten sonra başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ad05-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="5ad05-104">Çağrıları başlangıç <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmet sınıfı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="5ad05-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="5ad05-105">Genellikle, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmetin gerçekleştirecek yararlı çalışmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ad05-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="5ad05-106">Bir hizmeti başlatıldıktan sonra el ile duraklatıldı veya durduruluncaya kadar etkin kalır.</span><span class="sxs-lookup"><span data-stu-id="5ad05-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="5ad05-107">Hizmetleri otomatik olarak veya el ile başlatmak için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5ad05-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="5ad05-108">Yüklü olduğu bilgisayarın yeniden başlatılmasıyla ya da ilk açık olduğunda otomatik olarak başlayan bir hizmeti başlatılır.</span><span class="sxs-lookup"><span data-stu-id="5ad05-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="5ad05-109">Bir kullanıcı el ile başlayan bir hizmetin başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ad05-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ad05-110">Varsayılan olarak, Visual Studio ile oluşturulan hizmetleri el ile başlatmak için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5ad05-110">By default, services created with Visual Studio are set to start manually.</span></span>  
  
 <span data-ttu-id="5ad05-111">Bir hizmeti el ile başlatabilirsiniz birkaç yolu vardır: gelen **Sunucu Gezgini**, gelen **Hizmet Denetim Yöneticisi**, veya bir bileşen kullanarak koddan çağrılan <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="5ad05-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="5ad05-112">Ayarladığınız <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özellikte <xref:System.ServiceProcess.ServiceInstaller> bir hizmeti el ile veya otomatik olarak başlatılıp başlatılmayacağını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="5ad05-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="5ad05-113">Bir hizmetin nasıl başlaması gerektiğini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="5ad05-113">To specify how a service should start</span></span>  
  
1.  <span data-ttu-id="5ad05-114">Hizmetinizi oluşturduktan sonra onun için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5ad05-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="5ad05-115">Daha fazla bilgi için bkz: [nasıl yapılır: Hizmet uygulamanız için yükleyiciler ekleme](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="5ad05-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="5ad05-116">Tasarımcısı'nda çalıştığınız hizmeti için hizmet Yükleyici'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5ad05-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3.  <span data-ttu-id="5ad05-117">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini şunlardan biri:</span><span class="sxs-lookup"><span data-stu-id="5ad05-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="5ad05-118">Hizmetinizin yüklemesini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="5ad05-118">To have your service install</span></span>|<span data-ttu-id="5ad05-119">Bu değeri ayarlayın</span><span class="sxs-lookup"><span data-stu-id="5ad05-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="5ad05-120">Bilgisayar ne zaman yeniden</span><span class="sxs-lookup"><span data-stu-id="5ad05-120">When the computer is restarted</span></span>|<span data-ttu-id="5ad05-121">**Otomatik**</span><span class="sxs-lookup"><span data-stu-id="5ad05-121">**Automatic**</span></span>|  
    |<span data-ttu-id="5ad05-122">Açık bir kullanıcı eylem hizmeti başladığında</span><span class="sxs-lookup"><span data-stu-id="5ad05-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="5ad05-123">**El ile**</span><span class="sxs-lookup"><span data-stu-id="5ad05-123">**Manual**</span></span>|  
  
    > [!TIP]
    >  <span data-ttu-id="5ad05-124">Hiç başlatılan hizmetinizi önlemek için ayarlayabileceğiniz <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğine **devre dışı**.</span><span class="sxs-lookup"><span data-stu-id="5ad05-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="5ad05-125">Bir sunucunun yeniden başlatılması birkaç kez geçiyor ve normal şekilde başlamasını başlarsınız Hizmetleri engelleyerek zamandan tasarruf etmek istiyorsanız bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ad05-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ad05-126">Hizmetinizi yüklendikten sonra bu ve diğer özellikleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5ad05-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="5ad05-127">Sahip bir hizmeti başlatmak çeşitli yolları vardır, <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> işlem kümesine **el ile** — gelen **Sunucu Gezgini**, gelen **Windows Hizmet Denetimi Yöneticisi**, veya koddan.</span><span class="sxs-lookup"><span data-stu-id="5ad05-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="5ad05-128">Gerçekte bağlamında hizmeti bu yöntemler tüm başlatmak dikkate almak önemlidir **Hizmet Denetim Yöneticisi**; **Sunucu Gezgini** ve hizmet başlatma programlama yöntemleri gerçekte denetleyici.</span><span class="sxs-lookup"><span data-stu-id="5ad05-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="5ad05-129">Server Explorer'dan el ile bir hizmeti başlatmak için</span><span class="sxs-lookup"><span data-stu-id="5ad05-129">To manually start a service from Server Explorer</span></span>  
  
1.  <span data-ttu-id="5ad05-130">İçinde **Sunucu Gezgini**, zaten listede yoksa istediğiniz sunucuyu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5ad05-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="5ad05-131">Daha fazla bilgi için bkz: nasıl yapılır: erişim ve Sunucu Gezgini veritabanı Gezgini başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="5ad05-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2.  <span data-ttu-id="5ad05-132">Genişletme **Hizmetleri** düğümünü ve ardından başlatmak istiyor hizmetini bulun.</span><span class="sxs-lookup"><span data-stu-id="5ad05-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3.  <span data-ttu-id="5ad05-133">Hizmet adını sağ tıklatın ve **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="5ad05-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="5ad05-134">El ile bir hizmeti Hizmet Denetim Yöneticisi'nden başlatmak için</span><span class="sxs-lookup"><span data-stu-id="5ad05-134">To manually start a service from Services Control Manager</span></span>  
  
1.  <span data-ttu-id="5ad05-135">Açık **Hizmet Denetim Yöneticisi** aşağıdakilerden birini yaparak:</span><span class="sxs-lookup"><span data-stu-id="5ad05-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    -   <span data-ttu-id="5ad05-136">Windows XP ve 2000 Professional, sağ **Bilgisayarım** Masaüstü ve ardından **Yönet**.</span><span class="sxs-lookup"><span data-stu-id="5ad05-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="5ad05-137">Görüntülenen iletişim kutusunda genişletin **hizmetler ve uygulamalar** düğümü.</span><span class="sxs-lookup"><span data-stu-id="5ad05-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="5ad05-138">\- veya -</span><span class="sxs-lookup"><span data-stu-id="5ad05-138">\- or -</span></span>  
  
    -   <span data-ttu-id="5ad05-139">Windows Server 2003 ve Windows 2000 Server'ı tıklatın **Başlat**, işaret **programları**, tıklatın **Yönetimsel Araçlar**ve ardından **Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="5ad05-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ad05-140">Windows NT sürüm 4. 0'da, bu iletişim kutusundan açabilirsiniz **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="5ad05-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="5ad05-141">Listelenen hizmetinizi görmelisiniz **Hizmetleri** penceresinin bölümü.</span><span class="sxs-lookup"><span data-stu-id="5ad05-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2.  <span data-ttu-id="5ad05-142">Listeden hizmetinizi seçin, sağ tıklatın ve ardından **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="5ad05-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="5ad05-143">Bir hizmet kodundan el ile başlatmak için</span><span class="sxs-lookup"><span data-stu-id="5ad05-143">To manually start a service from code</span></span>  
  
1.  <span data-ttu-id="5ad05-144">Bir örneğini oluşturmak <xref:System.ServiceProcess.ServiceController> sınıfı ve yönetmek istediğiniz hizmet ile etkileşimde bulunacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="5ad05-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2.  <span data-ttu-id="5ad05-145">Çağrı <xref:System.ServiceProcess.ServiceController.Start%2A> hizmetini başlatmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="5ad05-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad05-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ad05-146">See Also</span></span>  
 [<span data-ttu-id="5ad05-147">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="5ad05-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="5ad05-148">Nasıl Yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ad05-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="5ad05-149">Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="5ad05-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
