---
title: 'Nasıl yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama'
description: Diğer Visual Studio uygulama türleri olarak hata ayıklama yapmak için basit olmayan Windows hizmeti uygulamalarında hata ayıklamayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: fb58f2ff4f480347f0f233ecd9a619cf287cfdfd
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925767"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="f0864-103">Nasıl yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f0864-103">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="f0864-104">Bir hizmet, Visual Studio 'nun içinden değil, hizmetler Denetim Yöneticisi bağlamı içinden çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0864-104">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="f0864-105">Bu nedenle, bir hizmetin hata ayıklaması, diğer Visual Studio Uygulama türlerinde hata ayıklama kadar basit değildir.</span><span class="sxs-lookup"><span data-stu-id="f0864-105">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="f0864-106">Bir hizmette hata ayıklamak için hizmeti başlatmanız ve sonra çalıştığı işleme bir hata ayıklayıcı bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0864-106">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="f0864-107">Daha sonra Visual Studio 'nun tüm standart hata ayıklama işlevselliğini kullanarak uygulamanızda hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0864-107">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f0864-108">İşlemin ne olduğunu bilmiyorsanız bir işleme iliştirmemelisiniz ve bu işlemi, büyük olasılıkla bu süreci sonlandırmanız ve muhtemelen sonlandırmasına ilişkin sonuçları anlamadığınız sürece.</span><span class="sxs-lookup"><span data-stu-id="f0864-108">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="f0864-109">Örneğin, WinLogon işlemine ekler ve ardından hata ayıklamayı durdurursanız, sistem WinLogon olmadan çalışamadığı için sistem durur.</span><span class="sxs-lookup"><span data-stu-id="f0864-109">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="f0864-110">Hata ayıklayıcıyı yalnızca çalışan bir hizmete ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0864-110">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="f0864-111">Ek işlemi, hizmetinizin geçerli çalışmasını keser; hizmetin işlemesini gerçekten durdurmaz veya duraklatmaz.</span><span class="sxs-lookup"><span data-stu-id="f0864-111">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="f0864-112">Diğer bir deyişle, hizmetiniz hata ayıklamaya başladığınızda çalışıyorsa, hata ayıkladığınızda hala çalışmaya devam eder ancak işlem askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="f0864-112">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="f0864-113">İşleme iliştirdikten sonra kesme noktaları ayarlayabilir ve kodunuzda hata ayıklamak için bunları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0864-113">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="f0864-114">İşleme iliştirmek için kullandığınız iletişim kutusundan çıktıktan sonra, hata ayıklama modunda etkin bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="f0864-114">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="f0864-115">Service Control Manager 'ı kullanarak hizmetinizi başlatabilir, durdurabilir, duraklatabilir ve devam edebilir, böylece ayarladığınız kesme noktalarına vurulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="f0864-115">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="f0864-116">Hata ayıklama başarılı olduktan sonra bu kukla hizmeti daha sonra kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0864-116">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="f0864-117">Bu makalede, yerel bilgisayarda çalışan bir hizmetin hata ayıklaması ele alınmaktadır, ancak uzak bir bilgisayarda çalışan Windows hizmetlerinde de hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0864-117">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="f0864-118">Bkz. [Uzaktan hata ayıklama](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="f0864-118">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0864-119"><xref:System.ServiceProcess.ServiceBase.OnStart%2A>Service Control Manager bir hizmeti başlatmaya yönelik tüm denemelerde 30 saniyelik bir sınır sağladığından metodun hata ayıklaması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f0864-119">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="f0864-120">Daha fazla bilgi için bkz. [sorun giderme: Windows hizmetlerinde hata ayıklama](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0864-120">For more information, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f0864-121">Hata ayıklama ile ilgili anlamlı bilgiler almak için, Visual Studio hata ayıklayıcının ayıklanmakta olan ikililerin sembol dosyalarını bulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0864-121">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="f0864-122">Visual Studio 'da oluşturduğunuz bir hizmette hata ayıklaması yapıyorsanız, sembol dosyaları (. pdb dosyaları) yürütülebilir veya kitaplıkla aynı klasörde bulunur ve hata ayıklayıcı bunları otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="f0864-122">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="f0864-123">Derlemediğiniz bir hizmette hata ayıklaması yapıyorsanız, öncelikle hizmetin sembollerini bulmalı ve hata ayıklayıcı tarafından bulunduklarında emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0864-123">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="f0864-124">Bkz. [Visual Studio hata ayıklayıcısında simge (. pdb) ve kaynak dosyaları belirtme](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="f0864-124">See [Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span> <span data-ttu-id="f0864-125">Bir sistem işleminde hata ayıklaması yapıyorsanız veya hizmetinizdeki Sistem çağrılarına yönelik simgelere sahip olmak istiyorsanız, Microsoft sembol sunucularını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0864-125">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="f0864-126">Bkz. [hata ayıklama sembolleri](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="f0864-126">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="f0864-127">Bir hizmette hata ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="f0864-127">To debug a service</span></span>  
  
1. <span data-ttu-id="f0864-128">Hata ayıklama yapılandırmasında hizmetinizi derleyin.</span><span class="sxs-lookup"><span data-stu-id="f0864-128">Build your service in the Debug configuration.</span></span>  
  
2. <span data-ttu-id="f0864-129">Hizmetinizi yükler.</span><span class="sxs-lookup"><span data-stu-id="f0864-129">Install your service.</span></span> <span data-ttu-id="f0864-130">Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0864-130">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
3. <span data-ttu-id="f0864-131">Hizmetinizi, hizmet **Denetim Yöneticisi**'nden, **Sunucu Gezgini**veya koddan başlatın.</span><span class="sxs-lookup"><span data-stu-id="f0864-131">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="f0864-132">Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri başlatma](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0864-132">For more information, see [How to: Start Services](how-to-start-services.md).</span></span>  
  
4. <span data-ttu-id="f0864-133">Sistem işlemlerine iliştirebilmeniz için Visual Studio 'Yu yönetici kimlik bilgileriyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="f0864-133">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5. <span data-ttu-id="f0864-134">Seçim Visual Studio menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f0864-134">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="f0864-135">**Seçenekler** iletişim kutusunda, **hata ayıklama**, **semboller**' i seçin, **Microsoft sembol sunucuları** onay kutusunu seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f0864-135">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6. <span data-ttu-id="f0864-136">Menü çubuğunda, **Hata Ayıkla** veya **Araçlar** menüsünden **İşleme İliştir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f0864-136">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="f0864-137">(Klavye: Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="f0864-137">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="f0864-138">**Süreçler** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f0864-138">The **Processes** dialog box appears.</span></span>  
  
7. <span data-ttu-id="f0864-139">**Tüm kullanıcılardan Işlem göster** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="f0864-139">Select the **Show processes from all users** check box.</span></span>  
  
8. <span data-ttu-id="f0864-140">**Kullanılabilir işlemler** bölümünde hizmetinize yönelik işlemi seçin ve ardından **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f0864-140">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="f0864-141">İşlem hizmetinize ait yürütülebilir dosya ile aynı ada sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f0864-141">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="f0864-142">**Işleme İliştir** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f0864-142">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="f0864-143">Uygun seçenekleri belirleyin ve ardından iletişim kutusunu kapatmak için **Tamam** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f0864-143">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f0864-144">Artık hata ayıklama modundasınız.</span><span class="sxs-lookup"><span data-stu-id="f0864-144">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="f0864-145">Kodunuzda kullanmak istediğiniz kesme noktalarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f0864-145">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="f0864-146">Hizmet Denetim Yöneticisi 'Ne erişin ve hizmetinizi değiştirin, durdur, Duraklat ve devam et komutlarını göndererek kesme noktalarınıza ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="f0864-146">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="f0864-147">Hizmetler Denetim Yöneticisi 'ni çalıştırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri başlatma](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0864-147">For more information about running the Services Control Manager, see [How to: Start Services](how-to-start-services.md).</span></span> <span data-ttu-id="f0864-148">Ayrıca bkz. [sorun giderme: Windows hizmetlerinde hata ayıklama](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0864-148">Also, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="f0864-149">Windows Hizmetleri için hata ayıklama Ipuçları</span><span class="sxs-lookup"><span data-stu-id="f0864-149">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="f0864-150">Hizmetin işlemine iliştirme, bu hizmet için kodun tümünü değil, çoğu hata ayıklamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f0864-150">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="f0864-151">Örneğin, hizmet zaten başlatılmış olduğundan, hizmetin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemindeki kodda veya `Main` hizmeti bu şekilde yüklemek için kullanılan yöntemdeki kodda hata ayıklayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f0864-151">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="f0864-152">Bu sınırlamaya geçici çözüm sağlamanın bir yolu, hizmet uygulamanızda yalnızca hata ayıklamaya yardımcı olmak için olan geçici bir ikinci hizmet oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="f0864-152">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="f0864-153">Her iki hizmeti de yükleyebilir ve ardından hizmet sürecini yüklemek için bu kukla hizmeti başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0864-153">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="f0864-154">Geçici hizmet işlemi başlatduktan sonra, hizmet işlemine iliştirmek için Visual Studio 'daki **hata ayıklama** menüsünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0864-154">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="f0864-155"><xref:System.Threading.Thread.Sleep%2A>İşleme iliştirebilmeniz için, eyleme çağrı eklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="f0864-155">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="f0864-156">Programı bir normal konsol uygulamasına değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="f0864-156">Try changing the program to a regular console application.</span></span> <span data-ttu-id="f0864-157">Bunu yapmak için `Main` yöntemi, nasıl başlatıldığına bağlı olarak hem Windows hizmeti hem de konsol uygulaması olarak çalıştırabilmeniz için aşağıdaki gibi yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="f0864-157">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="f0864-158">Nasıl yapılır: bir Windows hizmetini konsol uygulaması olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f0864-158">How to: Run a Windows Service as a console application</span></span>  
  
1. <span data-ttu-id="f0864-159">Hizmetinize ve yöntemlerini çalıştıran bir yöntem ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> :</span><span class="sxs-lookup"><span data-stu-id="f0864-159">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. <span data-ttu-id="f0864-160">`Main`Yöntemi aşağıdaki gibi yeniden yazın:</span><span class="sxs-lookup"><span data-stu-id="f0864-160">Rewrite the `Main` method as follows:</span></span>  
  
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
  
3. <span data-ttu-id="f0864-161">Projenin özelliklerinin **uygulama** sekmesinde, **çıkış türünü** **konsol uygulaması**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f0864-161">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4. <span data-ttu-id="f0864-162">**Hata ayıklamayı Başlat** (F5) seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="f0864-162">Choose **Start Debugging** (F5).</span></span>  
  
5. <span data-ttu-id="f0864-163">Programı yeniden bir Windows hizmeti olarak çalıştırmak için, uygulamayı yükleyip Windows hizmeti için her zamanki gibi başlatın.</span><span class="sxs-lookup"><span data-stu-id="f0864-163">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="f0864-164">Bu değişiklikleri tersine çevirmek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f0864-164">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="f0864-165">Bazı durumlarda, örneğin yalnızca sistem başlangıcında oluşan bir sorunu ayıklamak istediğinizde, Windows hata ayıklayıcıyı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0864-165">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="f0864-166">[Windows Sürücü Seti 'ni (WDK) indirin](/windows-hardware/drivers/download-the-wdk) ve bkz. [Windows hizmetlerinde hata ayıklama](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="f0864-166">[Download the Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0864-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0864-167">See also</span></span>

- [<span data-ttu-id="f0864-168">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="f0864-168">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="f0864-169">Nasıl yapılır: Hizmetleri Yükleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="f0864-169">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="f0864-170">Nasıl yapılır: Hizmetleri Başlatma</span><span class="sxs-lookup"><span data-stu-id="f0864-170">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="f0864-171">Bir hizmette hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f0864-171">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
