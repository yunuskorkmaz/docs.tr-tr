---
title: 'Nasıl Yapılır: Hizmetleri Başlatma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: b3f04deb11a23957198864c444b4872aef45b2e4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176753"
---
# <a name="how-to-start-services"></a><span data-ttu-id="b1f95-102">Nasıl Yapılır: Hizmetleri Başlatma</span><span class="sxs-lookup"><span data-stu-id="b1f95-102">How to: Start Services</span></span>
<span data-ttu-id="b1f95-103">Bir hizmeti yüklendikten sonra başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1f95-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="b1f95-104">Çağrı <xref:System.ServiceProcess.ServiceBase.OnStart%2A> hizmet sınıfı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b1f95-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="b1f95-105">Genellikle, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> hizmetin gerçekleştirecek faydalı bir iş yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1f95-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="b1f95-106">Bir hizmeti başlatıldıktan sonra el ile duraklatıldı veya durduruluncaya kadar etkin kalır.</span><span class="sxs-lookup"><span data-stu-id="b1f95-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="b1f95-107">Hizmetleri otomatik olarak veya el ile başlatmak için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b1f95-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="b1f95-108">Yüklü olduğu bilgisayarın yeniden başlatılmasıyla ya da önce açık olduğunda otomatik olarak başlatan bir hizmet başlatılır.</span><span class="sxs-lookup"><span data-stu-id="b1f95-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="b1f95-109">Bir kullanıcı el ile başlayan bir hizmetin başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f95-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1f95-110">Varsayılan olarak, Visual Studio ile oluşturulan hizmetleri el ile başlatmak için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b1f95-110">By default, services created with Visual Studio are set to start manually.</span></span>  
  
 <span data-ttu-id="b1f95-111">Bir hizmeti el ile başlatabilir birkaç yolu vardır — dan **Sunucu Gezgini**, gelen **Hizmet Denetim Yöneticisi**, veya koddan bir bileşen kullanma adlı <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="b1f95-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="b1f95-112">Ayarladığınız <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği <xref:System.ServiceProcess.ServiceInstaller> bir hizmeti elle veya otomatik olarak başlatılıp başlatılmayacağını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="b1f95-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="b1f95-113">Bir hizmetin nasıl başlaması gerektiğini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="b1f95-113">To specify how a service should start</span></span>  
  
1.  <span data-ttu-id="b1f95-114">Hizmetinizi oluşturduktan sonra bunun için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1f95-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="b1f95-115">Daha fazla bilgi için [nasıl yapılır: Hizmet uygulamanız için yükleyicileri ekleyin](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="b1f95-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="b1f95-116">Tasarımcısı'nda çalıştığınız hizmeti için hizmet Yükleyici'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b1f95-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3.  <span data-ttu-id="b1f95-117">İçinde **özellikleri** penceresinde <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini aşağıdakilerden biri:</span><span class="sxs-lookup"><span data-stu-id="b1f95-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="b1f95-118">Hizmetinizi yüklemek için</span><span class="sxs-lookup"><span data-stu-id="b1f95-118">To have your service install</span></span>|<span data-ttu-id="b1f95-119">Bu değeri ayarlayın</span><span class="sxs-lookup"><span data-stu-id="b1f95-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="b1f95-120">Bilgisayarın ne zaman yeniden başlatılır</span><span class="sxs-lookup"><span data-stu-id="b1f95-120">When the computer is restarted</span></span>|<span data-ttu-id="b1f95-121">**Otomatik**</span><span class="sxs-lookup"><span data-stu-id="b1f95-121">**Automatic**</span></span>|  
    |<span data-ttu-id="b1f95-122">Bir açık kullanıcı eylemi hizmeti başladığında</span><span class="sxs-lookup"><span data-stu-id="b1f95-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="b1f95-123">**El ile**</span><span class="sxs-lookup"><span data-stu-id="b1f95-123">**Manual**</span></span>|  
  
    > [!TIP]
    >  <span data-ttu-id="b1f95-124">Hizmetinizi hiç çalışmaya önlemek için ayarlayabileceğiniz <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliğini **devre dışı bırakılmış**.</span><span class="sxs-lookup"><span data-stu-id="b1f95-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="b1f95-125">Bir sunucuyu birkaç kez yeniden olacak ve normalde başlatılması başlar Hizmetleri engelleyerek zamandan tasarruf yapmak istiyorsanız bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f95-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1f95-126">Hizmet yüklendikten sonra bu ve diğer özellikleri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b1f95-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="b1f95-127">Bir hizmet başlangıç birkaç yolu vardır, <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> işlem kümesine **el ile** — gelen **Sunucu Gezgini**, gelen **Windows Hizmet Denetim Yöneticisi**, veya koddan.</span><span class="sxs-lookup"><span data-stu-id="b1f95-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="b1f95-128">Aslında bağlamında hizmeti tüm bu yöntemleri başlatmak dikkat edin önemlidir **Hizmet Denetim Yöneticisi**; **Sunucu Gezgini** ve hizmet başlatma programlı yöntemlerle gerçekten işlemek denetleyici.</span><span class="sxs-lookup"><span data-stu-id="b1f95-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="b1f95-129">El ile bir hizmeti sunucu Gezgini'nden başlatmak için</span><span class="sxs-lookup"><span data-stu-id="b1f95-129">To manually start a service from Server Explorer</span></span>  
  
1.  <span data-ttu-id="b1f95-130">İçinde **Sunucu Gezgini**, zaten listede yoksa istediğiniz sunucuya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1f95-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="b1f95-131">Daha fazla bilgi için bkz: nasıl yapılır: erişim ve Sunucu Gezgini veritabanı Gezgini başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b1f95-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2.  <span data-ttu-id="b1f95-132">Genişletin **Hizmetleri** düğümünü ve ardından başlamak istediğiniz hizmeti bulun.</span><span class="sxs-lookup"><span data-stu-id="b1f95-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3.  <span data-ttu-id="b1f95-133">Hizmet adını sağ tıklayın ve **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="b1f95-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="b1f95-134">El ile bir hizmeti Hizmet Denetim Yöneticisi'nden başlatmak için</span><span class="sxs-lookup"><span data-stu-id="b1f95-134">To manually start a service from Services Control Manager</span></span>  
  
1.  <span data-ttu-id="b1f95-135">Açık **Hizmet Denetim Yöneticisi** aşağıdakilerden birini yaparak:</span><span class="sxs-lookup"><span data-stu-id="b1f95-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    -   <span data-ttu-id="b1f95-136">Windows XP ve 2000 Professional, sağ **Bilgisayarım** Masaüstü ve ardından **Yönet**.</span><span class="sxs-lookup"><span data-stu-id="b1f95-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="b1f95-137">Görüntülenen iletişim kutusunda Genişlet **hizmetler ve uygulamalar** düğümü.</span><span class="sxs-lookup"><span data-stu-id="b1f95-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="b1f95-138">\- veya -</span><span class="sxs-lookup"><span data-stu-id="b1f95-138">\- or -</span></span>  
  
    -   <span data-ttu-id="b1f95-139">Windows Server 2003 ve Windows 2000 Server **Başlat**, işaret **programlar**, tıklayın **Yönetimsel Araçlar**ve ardından **Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="b1f95-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b1f95-140">Windows NT sürüm 4. 0'da, bu iletişim kutusundan açabilirsiniz **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="b1f95-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="b1f95-141">Hizmetiniz listede görmelisiniz **Hizmetleri** pencerenin.</span><span class="sxs-lookup"><span data-stu-id="b1f95-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2.  <span data-ttu-id="b1f95-142">Listeden hizmetinizi seçin, sağ tıklayın ve ardından **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="b1f95-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="b1f95-143">Bir hizmeti koddan el ile başlatmak için</span><span class="sxs-lookup"><span data-stu-id="b1f95-143">To manually start a service from code</span></span>  
  
1.  <span data-ttu-id="b1f95-144">Bir örneğini oluşturmak <xref:System.ServiceProcess.ServiceController> sınıfı ve yönetmek istediğiniz hizmetiyle etkileşim kurmak üzere yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b1f95-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2.  <span data-ttu-id="b1f95-145">Çağrı <xref:System.ServiceProcess.ServiceController.Start%2A> hizmeti başlatmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b1f95-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f95-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1f95-146">See Also</span></span>  
 [<span data-ttu-id="b1f95-147">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="b1f95-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="b1f95-148">Nasıl Yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1f95-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="b1f95-149">Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="b1f95-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
