---
title: 'Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
manager: douge
ms.openlocfilehash: 5de4c90361033df603bb63fbb365514d6bb5ea0c
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752324"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="0b676-102">Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0b676-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="0b676-103">Bir hizmet alanından, Hizmet Denetim Yöneticisi yerine içinden bağlam içinde çalıştırılmalıdır Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b676-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="0b676-104">Bu nedenle, bir hizmette hata ayıklamak diğer Visual Studio uygulama türlerinde hata ayıklamak kadar basit değil</span><span class="sxs-lookup"><span data-stu-id="0b676-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="0b676-105">Bir hizmette hata ayıklamak için hizmeti başlatın ve sonra içinde çalıştığı işleme bir hata ayıklayıcı eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b676-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="0b676-106">Ardından tüm Visual Studio standart hata ayıklama işlevselliğini kullanarak uygulamanızın hatalarını ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b676-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="0b676-107">Hangi işlemin ve büyük olasılıkla, işlemi öldürmenin ve işleme ekleme sonuçları anladığınızdan bilmediği sürece bir işleme eklememelisiniz.</span><span class="sxs-lookup"><span data-stu-id="0b676-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="0b676-108">Örneğin, WinLogon işlemine eklerseniz ardından hata ayıklamayı durdurmak, WinLogon işleyemeyeceği sistem durdurulur.</span><span class="sxs-lookup"><span data-stu-id="0b676-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="0b676-109">Hata ayıklayıcıyı yalnızca çalışan bir hizmete ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b676-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="0b676-110">Ek işlemi, hizmetinizin geçerli işleyişini keser; Bu değil gerçekten durdurmaz veya duraklatmaz.</span><span class="sxs-lookup"><span data-stu-id="0b676-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="0b676-111">Hata ayıklamayı başladığınızda, hizmet çalışıyorsa, diğer bir deyişle, bu teknik olarak hala başlatılmış durumdadır ayıklama, ancak işlemesi askıya aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0b676-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="0b676-112">İşleme iliştirdikten sonra kesme noktaları ayarlayabilir ve bunları kodunuzdaki hataları ayıklamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="0b676-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="0b676-113">İşleme için kullandığınız iletişim kutusundan çıktıktan sonra etkili bir şekilde hata ayıklama modunda olursunuz.</span><span class="sxs-lookup"><span data-stu-id="0b676-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="0b676-114">Başlatma, durdurma, duraklatma ve böylece ayarladığınız kesme noktalarının isabet hizmetiniz, devam etmek için Hizmet Denetim Yöneticisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b676-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="0b676-115">Hata ayıklama başarılı olduktan sonra bu kukla hizmetini daha sonra kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b676-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="0b676-116">Bu makalede yerel bilgisayar üzerinde çalışan bir hizmette hata ayıklamak yer almaktadır, ancak uzak bir bilgisayarda çalışan Windows Hizmetleri de ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b676-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="0b676-117">Bkz: [uzaktan hata ayıklama](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="0b676-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b676-118">Hata ayıklama <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 30 saniyelik bir sınır üzerinde bir hizmet başlatmaya yönelik tüm girişimleri Hizmet Denetim Yöneticisi'ni getirir çünkü yöntemi zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b676-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="0b676-119">Daha fazla bilgi için [sorunlarını giderme: Windows Hizmetleri hata ayıklama](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b676-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0b676-120">Hata ayıklama için anlamlı bilgiler almak için Visual Studio hata ayıklayıcının, hatası ayıklanan ikililer için Sembol dosyalarını bulmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b676-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="0b676-121">Visual Studio'da oluşturulan bir hizmet ayıklıyorsanız, sembol dosyalarını (.pdb) yürütülebilir veya kitaplık aynı klasörde olan ve hata ayıklayıcının bunları otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="0b676-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="0b676-122">Yapı gelmedi bir hizmeti hata ayıklaması yapıyorsanız, ilk hizmet için simgeleri Bul ve hata ayıklayıcı tarafından bulunabilir emin olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b676-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="0b676-123">Bkz: [sembol (.pdb) belirtin ve kaynak dosyaları](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span><span class="sxs-lookup"><span data-stu-id="0b676-123">See [Specify Symbol (.pdb) and Source Files](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span></span> <span data-ttu-id="0b676-124">Bir sistem işlemi hata ayıklama veya sistem çağrıları için semboller hizmetlerinizde sahip olmasını isterseniz Microsoft sembol sunucuları eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b676-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="0b676-125">Bkz: [hata ayıklama simgeleri](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="0b676-125">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="0b676-126">Bir hizmette hata ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="0b676-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="0b676-127">Hizmetinizde hata ayıklama yapılandırmasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0b676-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="0b676-128">Hizmetinizi yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0b676-128">Install your service.</span></span> <span data-ttu-id="0b676-129">Daha fazla bilgi için [nasıl yapılır: yükleme ve kaldırma Hizmetleri](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b676-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="0b676-130">Başlat'nden ya da hizmetiniz **Hizmet Denetim Yöneticisi**, **Sunucu Gezgini**, veya koddan.</span><span class="sxs-lookup"><span data-stu-id="0b676-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="0b676-131">Daha fazla bilgi için [nasıl yapılır: hizmetlerini başlatma](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b676-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="0b676-132">Sistem işleme iliştirebilirsiniz için yönetici kimlik bilgileriyle Visual Studio'yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="0b676-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="0b676-133">(İsteğe bağlı) Visual Studio menü çubuğunda **Araçları**, **seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="0b676-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="0b676-134">İçinde **seçenekleri** iletişim kutusunda **hata ayıklama**, **sembolleri**seçin **Microsoft sembol sunucuları** onay kutusunu işaretleyin ve ardından **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="0b676-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="0b676-135">Menü çubuğunda, **iliştirme** gelen **hata ayıklama** veya **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="0b676-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="0b676-136">(Klavye: Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="0b676-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="0b676-137">**İşlemleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0b676-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="0b676-138">Seçin **tüm kullanıcıların işlemlerini göster** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="0b676-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="0b676-139">İçinde **kullanılabilir işlemler** bölümünde hizmetinizin işlemini seçin ve ardından **iliştirme**.</span><span class="sxs-lookup"><span data-stu-id="0b676-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="0b676-140">İşlem hizmetiniz için yürütülebilir dosyasıyla aynı ada sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0b676-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="0b676-141">**İliştirme** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0b676-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="0b676-142">Uygun seçenekleri seçin ve ardından **Tamam** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="0b676-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b676-143">Hata ayıklama modunda sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="0b676-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="0b676-144">Kodunuzda kullanmak istediğiniz herhangi bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0b676-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="0b676-145">Hizmet Denetim Yöneticisi erişim işleme hizmeti, gönderen durdurma, duraklatma ve devam et komutlarını kesme noktalarınıza isabet ettirmek için.</span><span class="sxs-lookup"><span data-stu-id="0b676-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="0b676-146">Hizmet Denetimi Yöneticisi'ni çalıştırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmetlerini başlatma](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b676-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="0b676-147">Ayrıca bkz [sorunlarını giderme: Windows Hizmetleri hata ayıklama](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b676-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="0b676-148">Windows Hizmetleri için hata ayıklama ipuçları</span><span class="sxs-lookup"><span data-stu-id="0b676-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="0b676-149">Hizmet işlemine iliştirme tümünü değil ancak bu hizmet için kod hatalarını ayıklamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b676-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="0b676-150">Örneğin, hizmet zaten başlatılmış olduğundan, hizmetin kodunda hata ayıklaması yapılamıyor <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi veya kodda `Main` bu şekilde hizmeti yüklemek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="0b676-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="0b676-151">Bu sınırlamaya geçici bir çözüm yollarından biri yalnızca hata ayıklamaya yardımcı olmak için mevcut hizmet uygulamanızda ikinci bir geçici hizmet oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0b676-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="0b676-152">İki hizmeti de yükleyebilir ve sonra hizmet işlemini yüklemek üzere bu kukla hizmetini başlatın.</span><span class="sxs-lookup"><span data-stu-id="0b676-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="0b676-153">Geçici hizmet işlemi başlattıktan sonra kullanabileceğiniz **hata ayıklama** hizmet işlemini iliştirmek için Visual Studio'da menü.</span><span class="sxs-lookup"><span data-stu-id="0b676-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="0b676-154">Çağrıları eklemeyi deneyin <xref:System.Threading.Thread.Sleep%2A> işleme olanağına kadar gecikme eylemi için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b676-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="0b676-155">Normal bir konsol programı değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="0b676-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="0b676-156">Bunu yapmak için yeniden `Main` şu şekilde bir Windows hizmeti olarak ve kullanmaya nasıl bağlı olarak bir konsol uygulaması olarak çalıştırabilmeniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b676-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="0b676-157">Nasıl yapılır: bir Windows hizmeti bir konsol uygulaması olarak çalıştır</span><span class="sxs-lookup"><span data-stu-id="0b676-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="0b676-158">Çalışan hizmetinize bir yöntem ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="0b676-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="0b676-159">Yeniden `Main` yöntemini aşağıdaki şekilde:</span><span class="sxs-lookup"><span data-stu-id="0b676-159">Rewrite the `Main` method as follows:</span></span>  
  
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
  
3.  <span data-ttu-id="0b676-160">İçinde **uygulama** sekmesinde projenin özelliklerini ayarlamak **çıkış türü** için **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="0b676-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="0b676-161">Seçin **hata ayıklamayı Başlat** (F5).</span><span class="sxs-lookup"><span data-stu-id="0b676-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="0b676-162">Program bir Windows hizmeti olarak yeniden çalıştırmak için yükleyin ve bir Windows hizmeti için her zamanki şekilde başlatın.</span><span class="sxs-lookup"><span data-stu-id="0b676-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="0b676-163">Bu değişiklikleri geri almak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0b676-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="0b676-164">Yalnızca sistem başlatma sırasında oluşan bir sorunu hata ayıklamak istediğiniz zaman gibi bazı durumlarda, Windows hata ayıklayıcı kullanmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="0b676-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="0b676-165">Yükleme [Windows için hata ayıklama araçları](http://msdn.microsoft.com/windows/hardware/hh852365) görüp [nasıl Windows hizmetlerinde hata ayıklama](http://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="0b676-165">Install [Debugging Tools for Windows](http://msdn.microsoft.com/windows/hardware/hh852365) and see [How to debug Windows Services](http://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b676-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b676-166">See Also</span></span>  
 [<span data-ttu-id="0b676-167">Windows Hizmeti Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="0b676-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="0b676-168">Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0b676-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="0b676-169">Nasıl Yapılır: Hizmetleri Başlatma</span><span class="sxs-lookup"><span data-stu-id="0b676-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="0b676-170">Hizmet hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0b676-170">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
