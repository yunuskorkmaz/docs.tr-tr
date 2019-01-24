---
title: 'Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: 02ea82bf224349e6ea7a5afbfb3c38ba50df46f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720372"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="5033c-102">Nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5033c-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="5033c-103">Bir hizmet alanından, Hizmet Denetim Yöneticisi yerine içinden bağlam içinde çalıştırılmalıdır Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5033c-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="5033c-104">Bu nedenle, bir hizmette hata ayıklamak diğer Visual Studio uygulama türlerinde hata ayıklamak kadar basit değil</span><span class="sxs-lookup"><span data-stu-id="5033c-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="5033c-105">Bir hizmette hata ayıklamak için hizmeti başlatın ve sonra içinde çalıştığı işleme bir hata ayıklayıcı eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5033c-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="5033c-106">Ardından tüm Visual Studio standart hata ayıklama işlevselliğini kullanarak uygulamanızın hatalarını ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5033c-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5033c-107">Hangi işlemin ve büyük olasılıkla, işlemi öldürmenin ve işleme ekleme sonuçları anladığınızdan bilmediği sürece bir işleme eklememelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5033c-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="5033c-108">Örneğin, WinLogon işlemine eklerseniz ardından hata ayıklamayı durdurmak, WinLogon işleyemeyeceği sistem durdurulur.</span><span class="sxs-lookup"><span data-stu-id="5033c-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="5033c-109">Hata ayıklayıcıyı yalnızca çalışan bir hizmete ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5033c-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="5033c-110">Ek işlemi, hizmetinizin geçerli işleyişini keser; Bu değil gerçekten durdurmaz veya duraklatmaz.</span><span class="sxs-lookup"><span data-stu-id="5033c-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="5033c-111">Hata ayıklamayı başladığınızda, hizmet çalışıyorsa, diğer bir deyişle, bu teknik olarak hala başlatılmış durumdadır ayıklama, ancak işlemesi askıya aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5033c-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="5033c-112">İşleme iliştirdikten sonra kesme noktaları ayarlayabilir ve bunları kodunuzdaki hataları ayıklamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5033c-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="5033c-113">İşleme için kullandığınız iletişim kutusundan çıktıktan sonra etkili bir şekilde hata ayıklama modunda olursunuz.</span><span class="sxs-lookup"><span data-stu-id="5033c-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="5033c-114">Başlatma, durdurma, duraklatma ve böylece ayarladığınız kesme noktalarının isabet hizmetiniz, devam etmek için Hizmet Denetim Yöneticisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5033c-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="5033c-115">Hata ayıklama başarılı olduktan sonra bu kukla hizmetini daha sonra kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5033c-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="5033c-116">Bu makalede yerel bilgisayar üzerinde çalışan bir hizmette hata ayıklamak yer almaktadır, ancak uzak bir bilgisayarda çalışan Windows Hizmetleri de ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5033c-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="5033c-117">Bkz: [uzaktan hata ayıklama](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="5033c-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5033c-118">Hata ayıklama <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 30 saniyelik bir sınır üzerinde bir hizmet başlatmaya yönelik tüm girişimleri Hizmet Denetim Yöneticisi'ni getirir çünkü yöntemi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="5033c-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="5033c-119">Daha fazla bilgi için [sorunlarını giderme: Windows hizmetlerinde hata ayıklama](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="5033c-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5033c-120">Hata ayıklama için anlamlı bilgiler almak için Visual Studio hata ayıklayıcının, hatası ayıklanan ikililer için Sembol dosyalarını bulmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="5033c-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="5033c-121">Visual Studio'da oluşturulan bir hizmet ayıklıyorsanız, sembol dosyalarını (.pdb) yürütülebilir veya kitaplık aynı klasörde olan ve hata ayıklayıcının bunları otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="5033c-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="5033c-122">Yapı gelmedi bir hizmeti hata ayıklaması yapıyorsanız, ilk hizmet için simgeleri Bul ve hata ayıklayıcı tarafından bulunabilir emin olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="5033c-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="5033c-123">Bkz: [sembol (.pdb) belirtin ve kaynak dosyaları](https://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span><span class="sxs-lookup"><span data-stu-id="5033c-123">See [Specify Symbol (.pdb) and Source Files](https://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span></span> <span data-ttu-id="5033c-124">Bir sistem işlemi hata ayıklama veya sistem çağrıları için semboller hizmetlerinizde sahip olmasını isterseniz Microsoft sembol sunucuları eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5033c-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="5033c-125">Bkz: [hata ayıklama simgeleri](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="5033c-125">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="5033c-126">Bir hizmette hata ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="5033c-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="5033c-127">Hizmetinizde hata ayıklama yapılandırmasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5033c-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="5033c-128">Hizmetinizi yükleyin.</span><span class="sxs-lookup"><span data-stu-id="5033c-128">Install your service.</span></span> <span data-ttu-id="5033c-129">Daha fazla bilgi için [nasıl yapılır: Hizmetleri Yükleme ve kaldırma](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="5033c-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="5033c-130">Başlat'nden ya da hizmetiniz **Hizmet Denetim Yöneticisi**, **Sunucu Gezgini**, veya koddan.</span><span class="sxs-lookup"><span data-stu-id="5033c-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="5033c-131">Daha fazla bilgi için [nasıl yapılır: Hizmetleri başlatmak](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="5033c-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="5033c-132">Sistem işleme iliştirebilirsiniz için yönetici kimlik bilgileriyle Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="5033c-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="5033c-133">(İsteğe bağlı) Visual Studio menü çubuğunda **Araçları**, **seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="5033c-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="5033c-134">İçinde **seçenekleri** iletişim kutusunda **hata ayıklama**, **sembolleri**seçin **Microsoft sembol sunucuları** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="5033c-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="5033c-135">Menü çubuğunda, **iliştirme** gelen **hata ayıklama** veya **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5033c-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="5033c-136">(Klavye: Ctrl+Alt+P)</span><span class="sxs-lookup"><span data-stu-id="5033c-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="5033c-137">**İşlemleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5033c-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="5033c-138">Seçin **tüm kullanıcıların işlemlerini göster** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="5033c-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="5033c-139">İçinde **kullanılabilir işlemler** bölümünde hizmetinizin işlemini seçin ve ardından **iliştirme**.</span><span class="sxs-lookup"><span data-stu-id="5033c-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="5033c-140">İşlem hizmetiniz için yürütülebilir dosyasıyla aynı ada sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5033c-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="5033c-141">**İliştirme** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5033c-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="5033c-142">Uygun seçenekleri seçin ve ardından **Tamam** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="5033c-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5033c-143">Hata ayıklama modunda sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5033c-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="5033c-144">Kodunuzda kullanmak istediğiniz herhangi bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5033c-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="5033c-145">Hizmet Denetim Yöneticisi erişim işleme hizmeti, gönderen durdurma, duraklatma ve devam et komutlarını kesme noktalarınıza isabet ettirmek için.</span><span class="sxs-lookup"><span data-stu-id="5033c-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="5033c-146">Hizmet Denetimi Yöneticisi'ni çalıştırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri başlatmak](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="5033c-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="5033c-147">Ayrıca bkz [sorunlarını giderme: Windows hizmetlerinde hata ayıklama](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="5033c-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="5033c-148">Windows Hizmetleri için hata ayıklama ipuçları</span><span class="sxs-lookup"><span data-stu-id="5033c-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="5033c-149">Hizmet işlemine iliştirme tümünü değil ancak bu hizmet için kod hatalarını ayıklamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5033c-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="5033c-150">Örneğin, hizmet zaten başlatılmış olduğundan, hizmetin kodunda hata ayıklaması yapılamıyor <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi veya kodda `Main` bu şekilde hizmeti yüklemek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="5033c-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="5033c-151">Bu sınırlamaya geçici bir çözüm yollarından biri yalnızca hata ayıklamaya yardımcı olmak için mevcut hizmet uygulamanızda ikinci bir geçici hizmet oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="5033c-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="5033c-152">İki hizmeti de yükleyebilir ve sonra hizmet işlemini yüklemek üzere bu kukla hizmetini başlatın.</span><span class="sxs-lookup"><span data-stu-id="5033c-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="5033c-153">Geçici hizmet işlemi başlattıktan sonra kullanabileceğiniz **hata ayıklama** hizmet işlemini iliştirmek için Visual Studio'da menü.</span><span class="sxs-lookup"><span data-stu-id="5033c-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="5033c-154">Çağrıları eklemeyi deneyin <xref:System.Threading.Thread.Sleep%2A> işleme olanağına kadar gecikme eylemi için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5033c-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="5033c-155">Normal bir konsol programı değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="5033c-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="5033c-156">Bunu yapmak için yeniden `Main` şu şekilde bir Windows hizmeti olarak ve kullanmaya nasıl bağlı olarak bir konsol uygulaması olarak çalıştırabilmeniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5033c-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="5033c-157">Nasıl yapılır: Bir Windows hizmeti bir konsol uygulaması olarak çalıştır</span><span class="sxs-lookup"><span data-stu-id="5033c-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="5033c-158">Çalışan hizmetinize bir yöntem ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="5033c-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="5033c-159">Yeniden `Main` yöntemini aşağıdaki şekilde:</span><span class="sxs-lookup"><span data-stu-id="5033c-159">Rewrite the `Main` method as follows:</span></span>  
  
    ```csharp  
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
    }
    ```  
  
3.  <span data-ttu-id="5033c-160">İçinde **uygulama** sekmesinde projenin özelliklerini ayarlamak **çıkış türü** için **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="5033c-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="5033c-161">Seçin **hata ayıklamayı Başlat** (F5).</span><span class="sxs-lookup"><span data-stu-id="5033c-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="5033c-162">Program bir Windows hizmeti olarak yeniden çalıştırmak için yükleyin ve bir Windows hizmeti için her zamanki şekilde başlatın.</span><span class="sxs-lookup"><span data-stu-id="5033c-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="5033c-163">Bu değişiklikleri geri almak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5033c-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="5033c-164">Yalnızca sistem başlatma sırasında oluşan bir sorunu hata ayıklamak istediğiniz zaman gibi bazı durumlarda, Windows hata ayıklayıcı kullanmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="5033c-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="5033c-165">Yükleme [Windows için hata ayıklama araçları](https://msdn.microsoft.com/windows/hardware/hh852365) görüp [nasıl Windows hizmetlerinde hata ayıklama](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="5033c-165">Install [Debugging Tools for Windows](https://msdn.microsoft.com/windows/hardware/hh852365) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5033c-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5033c-166">See also</span></span>
- [<span data-ttu-id="5033c-167">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="5033c-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="5033c-168">Nasıl yapılır: Hizmetleri Yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="5033c-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="5033c-169">Nasıl yapılır: Başlangıç Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5033c-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)
- [<span data-ttu-id="5033c-170">Hizmet hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5033c-170">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
