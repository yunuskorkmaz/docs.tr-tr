---
title: "Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: c49d05a9ca09a12044c0846db381368166e105bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="500c6-102">Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="500c6-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="500c6-103">Bir hizmet, hizmet denetimi Yöneticisi'ni yerine içinden bağlamında çalıştırılmak gerekir Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="500c6-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="500c6-104">Bir hizmet hata ayıklama özelliği bu nedenle, diğer Visual Studio uygulama türleri hata ayıklama olarak kadar basit değildir.</span><span class="sxs-lookup"><span data-stu-id="500c6-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="500c6-105">Bir hizmette hata ayıklamak için hizmeti başlatın ve sonra onu çalıştığı işlem bir hata ayıklayıcısı eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="500c6-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="500c6-106">Sonra tüm standart hata ayıklama işlevselliğini Visual Studio kullanarak uygulamanızı ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="500c6-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="500c6-107">Hangi işlemin ve ekleme ve büyük olasılıkla bu işlemin sonlandırılması sonuçlarını anlama bilmiyorsanız, bir işleme ek yapmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="500c6-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="500c6-108">Örneğin, WinLogon işleme ekleyin ve ardından hata ayıklamayı durdurun, WinLogon işleyemeyeceği sistem durdurulur.</span><span class="sxs-lookup"><span data-stu-id="500c6-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="500c6-109">Hata ayıklayıcı yalnızca çalışan bir hizmete ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="500c6-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="500c6-110">Ek işlemi geçerli işleyişini keser; gerçekte durdurmak veya hizmetin işleme duraklatmak değil.</span><span class="sxs-lookup"><span data-stu-id="500c6-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="500c6-111">Hata ayıklama başladığınızda, hizmet çalışıyorsa, diğer bir deyişle, bu teknik olarak hala başlatıldı ayıklama, ancak işleme askıya alındı olarak durumda.</span><span class="sxs-lookup"><span data-stu-id="500c6-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="500c6-112">İşleme ekledikten sonra kesme noktalarını ayarlayabilir ve bunlar kodunuzun hatalarını ayıklamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="500c6-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="500c6-113">İşleme iliştirilemiyor için kullandığınız iletişim kutusundan çıktıktan sonra etkin hata ayıklama modunda demektir.</span><span class="sxs-lookup"><span data-stu-id="500c6-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="500c6-114">Başlatma, durdurma, duraklatma ve böylece ayarladığınız kesme noktaları basarsa hizmetiniz, devam etmek için Hizmet Denetimi Yöneticisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="500c6-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="500c6-115">Hata ayıklama başarılı olduktan sonra daha sonra bu kukla hizmetini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="500c6-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="500c6-116">Bu makalede, yerel bilgisayarda çalışan bir hizmet hata ayıklama yer almaktadır, ancak uzak bir bilgisayarda çalışan Windows Hizmetleri de ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="500c6-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="500c6-117">Bkz: [uzaktan hata ayıklama](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="500c6-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="500c6-118">Hata ayıklama <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Hizmet Denetim Yöneticisi bir hizmeti başlatmak için tüm girişimleri üzerinde 30 saniyelik bir sınır getirir çünkü yöntemi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="500c6-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="500c6-119">Daha fazla bilgi için bkz: [sorun giderme: hata ayıklama Windows Hizmetleri](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="500c6-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="500c6-120">Hata ayıklama için anlamlı bilgiler almak için Visual Studio hata ayıklayıcısında simge dosyaları ayıklanacak ikili dosyaları bulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="500c6-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="500c6-121">Visual Studio'da yerleşik bir hizmet hata ayıklama, simge (.pdb dosyaları) yürütülebilir dosya veya kitaplığı olarak aynı klasörde dosyalardır ve hata ayıklayıcı bunları otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="500c6-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="500c6-122">Yapı gelmedi bir hizmet hata ayıklama, ilk sembolleri için hizmeti bulun ve gerekir hata ayıklayıcı tarafından bulunabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="500c6-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="500c6-123">Bkz: [simge (.pdb) belirtin ve kaynak dosyaları](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span><span class="sxs-lookup"><span data-stu-id="500c6-123">See [Specify Symbol (.pdb) and Source Files](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span></span> <span data-ttu-id="500c6-124">Bir sistem işlemi hatalarını ayıkladığınız veya sistem çağrıları simgelerini hizmetlerinizi içinde olmasını istiyorsanız, Microsoft simge sunucuları eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="500c6-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="500c6-125">Bkz: [hata ayıklama simgeleri](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).</span><span class="sxs-lookup"><span data-stu-id="500c6-125">See [Debugging Symbols](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="500c6-126">Bir hizmette hata ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="500c6-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="500c6-127">Hata ayıklama yapılandırmasını hizmetinizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="500c6-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="500c6-128">Hizmetinizi yükleyin.</span><span class="sxs-lookup"><span data-stu-id="500c6-128">Install your service.</span></span> <span data-ttu-id="500c6-129">Daha fazla bilgi için bkz: [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="500c6-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="500c6-130">Hizmetinizi herhangi birinden Başlat **Hizmet Denetim Yöneticisi**, **Sunucu Gezgini**, veya koddan.</span><span class="sxs-lookup"><span data-stu-id="500c6-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="500c6-131">Daha fazla bilgi için bkz: [nasıl yapılır: Hizmetleri başlatma](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="500c6-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="500c6-132">Sistem işlemleri ekleyebilirsiniz. böylece yönetici kimlik bilgileriyle Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="500c6-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="500c6-133">(İsteğe bağlı) Visual Studio menü çubuğunda seçin **Araçları**, **seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="500c6-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="500c6-134">İçinde **seçenekleri** iletişim kutusunda, seçin **hata ayıklama**, **simgeleri**seçin **Microsoft simge sunucuları** onay kutusunu işaretleyin ve ardından seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="500c6-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="500c6-135">Menü çubuğunda seçin **ekleme işlemi için** gelen **hata ayıklama** veya **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="500c6-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="500c6-136">(Klavye: Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="500c6-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="500c6-137">**İşlemleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="500c6-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="500c6-138">Seçin **işlemleri tüm kullanıcıları göster** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="500c6-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="500c6-139">İçinde **kullanılabilir işlemler** bölümünde, hizmetiniz için işlem seçin ve ardından **Attach**.</span><span class="sxs-lookup"><span data-stu-id="500c6-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="500c6-140">İşlem yürütülebilir dosyası hizmetiniz için aynı ada sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="500c6-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="500c6-141">**Ekleme işlemi için** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="500c6-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="500c6-142">Uygun seçenekleri seçin ve ardından **Tamam** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="500c6-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="500c6-143">Hata ayıklama modunda sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="500c6-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="500c6-144">Kodunuzda kullanmak istediğiniz tüm kesme noktalarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="500c6-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="500c6-145">Hizmet Denetim Yöneticisi erişim ve yönlendirme hizmeti, gönderen durdurma, duraklatma ve devam et noktalarınıza isabet komutlarını.</span><span class="sxs-lookup"><span data-stu-id="500c6-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="500c6-146">Hizmet Denetimi Yöneticisi'ni çalıştırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Hizmetleri başlatma](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="500c6-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="500c6-147">Ayrıca bkz [sorun giderme: hata ayıklama Windows Hizmetleri](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="500c6-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="500c6-148">Windows Hizmetleri için hata ayıklama ipuçları</span><span class="sxs-lookup"><span data-stu-id="500c6-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="500c6-149">Hizmetin işlemine iliştirme tümünün değil ancak bu hizmet için kod ayıklamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="500c6-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="500c6-150">Örneğin, hizmetin zaten başlatılmış olduğundan, hizmetin kodda hata ayıklama olamaz <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi veya kodda `Main` hizmeti bu şekilde yüklemek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="500c6-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="500c6-151">Bu sınırlamaya geçici bir çözüm yollarından biri yalnızca hata ayıklamaya yardımcı olmak için mevcut hizmet uygulamanızın geçici olarak ikinci hizmet oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="500c6-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="500c6-152">Her iki hizmet yükleyin ve ardından hizmet işlemini yüklemek için bu kukla hizmetini başlatın.</span><span class="sxs-lookup"><span data-stu-id="500c6-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="500c6-153">Geçici olarak hizmet işlemi başladıktan sonra kullanabileceğiniz **hata ayıklama** hizmet işlemini iliştirmek için Visual Studio menüsünde.</span><span class="sxs-lookup"><span data-stu-id="500c6-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="500c6-154">Çağrı eklemeyi deneyin <xref:System.Threading.Thread.Sleep%2A> işleme iliştirilemiyor mümkün kadar gecikme eylem yöntemi.</span><span class="sxs-lookup"><span data-stu-id="500c6-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="500c6-155">Program bir normal konsol uygulaması değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="500c6-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="500c6-156">Bunu yapmak için yeniden yazma `Main` şu şekilde bir Windows hizmeti hem nasıl başlatılacağını bağlı olarak bir konsol uygulaması olarak çalıştırabilmeniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="500c6-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="500c6-157">Nasıl yapılır: bir Windows hizmeti bir konsol uygulaması olarak çalıştırmak</span><span class="sxs-lookup"><span data-stu-id="500c6-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="500c6-158">Hizmetinize çalıştıran bir yöntem ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="500c6-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="500c6-159">Yeniden yazma `Main` yöntemini aşağıdaki şekilde:</span><span class="sxs-lookup"><span data-stu-id="500c6-159">Rewrite the `Main` method as follows:</span></span>  
  
    ```  
    static void Main(string[] args)  
            {  
                if (Environment.UserInteractive)  
                {  
                    MyNewService service1 = new MyNewService(args);  
                    service1.TestStartupAndStop(args);  
                }  
                else  
                {  
                    // Put the body of your old Main method here.  
                }  
    ```  
  
3.  <span data-ttu-id="500c6-160">İçinde **uygulama** projenin özelliklerinin sekmesinde ayarlamak **çıktı türü** için **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="500c6-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="500c6-161">Seçin **hata ayıklamayı Başlat** (F5).</span><span class="sxs-lookup"><span data-stu-id="500c6-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="500c6-162">Programı bir Windows hizmeti olarak yeniden çalıştırmak için yüklemek ve bir Windows hizmeti için her zamanki gibi başlatın.</span><span class="sxs-lookup"><span data-stu-id="500c6-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="500c6-163">Bu değişiklikleri geri almak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="500c6-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="500c6-164">Yalnızca sistem başlangıçta oluşan bir sorun hata ayıklamak istediğiniz zaman gibi bazı durumlarda, Windows hata ayıklayıcı kullanmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="500c6-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="500c6-165">Yükleme [Windows için hata ayıklama araçları](http://msdn.microsoft.com/windows/hardware/hh852365) ve [Windows Hizmetleri hata ayıklamak nasıl](http://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="500c6-165">Install [Debugging Tools for Windows](http://msdn.microsoft.com/windows/hardware/hh852365) and see [How to debug Windows Services](http://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="500c6-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="500c6-166">See Also</span></span>  
 [<span data-ttu-id="500c6-167">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="500c6-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="500c6-168">Nasıl yapılır: Hizmetleri Yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="500c6-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="500c6-169">Nasıl yapılır: Hizmetleri başlatma</span><span class="sxs-lookup"><span data-stu-id="500c6-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="500c6-170">Bir hizmet hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="500c6-170">Debugging a Service</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)
