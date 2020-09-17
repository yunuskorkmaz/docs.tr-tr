---
title: Kurulum Sorunlarını Giderme
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: fb687e9975ab9ac763030f10d54c7744dc02c9e0
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720458"
---
# <a name="troubleshoot-setup-issues"></a><span data-ttu-id="c9e67-102">Kurulum sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="c9e67-102">Troubleshoot setup issues</span></span>

<span data-ttu-id="c9e67-103">Bu makalede Windows Communication Foundation (WCF) kurulum sorunlarını nasıl giderebileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c9e67-103">This article describes how to troubleshoot Windows Communication Foundation (WCF) setup issues.</span></span>  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a><span data-ttu-id="c9e67-104">Bazı Windows Communication Foundation kayıt defteri anahtarları, .NET Framework 3,0 üzerinde MSI onarım Işlemi gerçekleştirerek onarılmıyor</span><span class="sxs-lookup"><span data-stu-id="c9e67-104">Some Windows Communication Foundation Registry Keys are not Repaired by Performing an MSI Repair Operation on the .NET Framework 3.0</span></span>  
 <span data-ttu-id="c9e67-105">Aşağıdaki kayıt defteri anahtarlarından birini silerseniz:</span><span class="sxs-lookup"><span data-stu-id="c9e67-105">If you delete any of the following registry keys:</span></span>  
  
- <span data-ttu-id="c9e67-106">HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="c9e67-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span></span>  
  
- <span data-ttu-id="c9e67-107">HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="c9e67-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span></span>  
  
- <span data-ttu-id="c9e67-108">HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="c9e67-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span></span>  
  
- <span data-ttu-id="c9e67-109">HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="c9e67-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span></span>  
  
- <span data-ttu-id="c9e67-110">HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\MSDTC Köprüsü 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="c9e67-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span></span>  
  
 <span data-ttu-id="c9e67-111">**Denetim Masası**'Ndaki **Program Ekle/kaldır** uygulamasından başlatılan .NET Framework 3,0 yükleyicisini kullanarak Onar 'ı çalıştırırsanız anahtarlar yeniden oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="c9e67-111">The keys are not re-created if you run repair by using the .NET Framework 3.0 installer launched from the **Add/Remove Programs** applet in **Control Panel**.</span></span> <span data-ttu-id="c9e67-112">Bu anahtarları doğru bir şekilde yeniden oluşturmak için, Kullanıcı .NET Framework 3,0 ' i kaldırmalı ve yeniden yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c9e67-112">To recreate these keys correctly, the user must uninstall and reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-wmi-provider"></a><span data-ttu-id="c9e67-113">WMI hizmeti bozulması, WMI sağlayıcısının yüklenmesini engelliyor</span><span class="sxs-lookup"><span data-stu-id="c9e67-113">WMI Service Corruption Blocks Installation of the WMI provider</span></span>

 <span data-ttu-id="c9e67-114">WMI hizmeti bozulması, .NET Framework 3,0 paketini yüklerken Windows Communication Foundation WMI sağlayıcısının yüklenmesini engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c9e67-114">WMI Service Corruption may block the installation of the Windows Communication Foundation WMI provider when installing the .NET Framework 3.0 package.</span></span> <span data-ttu-id="c9e67-115">Yükleme sırasında Windows Communication Foundation yükleyicisi, *mofcomp.exe* BILEŞENINI kullanarak WCF *. mof* dosyasını kaydedemiyor.</span><span class="sxs-lookup"><span data-stu-id="c9e67-115">During installation, the Windows Communication Foundation installer is unable to register the WCF *.mof* file using the *mofcomp.exe* component.</span></span> <span data-ttu-id="c9e67-116">Belirtilerin listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c9e67-116">The following is a list of symptoms:</span></span>  
  
1. <span data-ttu-id="c9e67-117">.NET Framework 3,0 yüklemesi başarıyla tamamlandı, ancak WCF WMI sağlayıcısı kayıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="c9e67-117">.NET Framework 3.0 installation completes successfully, but the WCF WMI provider is not registered.</span></span>  
  
2. <span data-ttu-id="c9e67-118">Uygulama olay günlüğünde, WCF için WMI sağlayıcısını kaydettirme veya mofcomp.exe çalıştırma sorunlarına başvuran bir hata olayı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c9e67-118">An error event appears in the application event log that references problems registering the WMI provider for WCF, or running mofcomp.exe.</span></span>  
  
3. <span data-ttu-id="c9e67-119">Kullanıcının% Temp% dizininde dd_wcf_retCA \* adlı kurulum günlük dosyası, WCF WMI sağlayıcısını kaydetme hatasına yönelik başvurular içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c9e67-119">The setup log file named dd_wcf_retCA\* in the user's %temp% directory contains references to failure to register the WCF WMI provider.</span></span>  
  
4. <span data-ttu-id="c9e67-120">Olay günlüğünde veya kurulum izleme günlük dosyasında aşağıdakiler gibi bir özel durum listelenebilir:</span><span class="sxs-lookup"><span data-stu-id="c9e67-120">An exception such as one the following may be listed in the event log or setup trace log file:</span></span>  
  
     <span data-ttu-id="c9e67-121">ServiceModelReg [11:09:59:046]: System. ApplicationException: beklenmeyen sonuç 3, "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" ile E:\WINDOWS\system32\wbem\mofcomp.exe yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="c9e67-121">ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"</span></span>  
  
     <span data-ttu-id="c9e67-122">veya:</span><span class="sxs-lookup"><span data-stu-id="c9e67-122">or:</span></span>  
  
     <span data-ttu-id="c9e67-123">ServiceModelReg [07:19:33:843]: System. TypeInitializationException: ' System. Management. ManagementPath ' için tür başlatıcısı özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="c9e67-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception.</span></span> <span data-ttu-id="c9e67-124">---> System. Runtime. InteropServices. COMException (0x80040154): CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} olan bileşen için COM sınıfı fabrikasını alma işlemi şu hata nedeniyle başarısız oldu: 80040154.</span><span class="sxs-lookup"><span data-stu-id="c9e67-124">---> System.Runtime.InteropServices.COMException (0x80040154): Retrieving the COM class factory for component with CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} failed due to the following error: 80040154.</span></span>  
  
     <span data-ttu-id="c9e67-125">veya:</span><span class="sxs-lookup"><span data-stu-id="c9e67-125">or:</span></span>  
  
     <span data-ttu-id="c9e67-126">ServiceModelReg [07:19:32:750]: System. ıO. FileNotFoundException: ' C:\WINDOWS\system32\wbem\mofcomp.exe ' dosyası veya bütünleştirilmiş kodu veya bağımlılıklarından biri yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="c9e67-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies.</span></span> <span data-ttu-id="c9e67-127">Sistem belirtilen dosyayı bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="c9e67-127">The system cannot find the file specified.</span></span>  
  
     <span data-ttu-id="c9e67-128">Dosya adı: ' C:\WINDOWS\system32\wbem\mofcomp.exe</span><span class="sxs-lookup"><span data-stu-id="c9e67-128">File name: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span></span>  
  
 <span data-ttu-id="c9e67-129">Daha önce açıklanan sorunu çözmek için aşağıdaki adımlar izlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c9e67-129">The following steps must be followed to resolve the problem described previously.</span></span>  
  
1. <span data-ttu-id="c9e67-130">WMI hizmetini onarmak için WMI Diagnosis Utility çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c9e67-130">Run the WMI Diagnosis Utility to repair the WMI service.</span></span> <span data-ttu-id="c9e67-131">Bu aracı kullanma hakkında daha fazla bilgi için bkz. [WMI diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span><span class="sxs-lookup"><span data-stu-id="c9e67-131">For more information about using this tool, see [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span></span>  
  
 <span data-ttu-id="c9e67-132">**Denetim Masası**'Nda bulunan **Program Ekle/kaldır** uygulamasını kullanarak .NET Framework 3,0 yüklemesini onarın veya .NET Framework 3,0 ' i kaldırın/yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="c9e67-132">Repair the .NET Framework 3.0 installation by using the **Add/Remove Programs** applet located in **Control Panel**, or uninstall/reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="repair-net-framework-30-after-net-framework-35-installation"></a><span data-ttu-id="c9e67-133">.NET Framework 3,5 yüklemesinden sonra .NET Framework 3,0 ' i Onar</span><span class="sxs-lookup"><span data-stu-id="c9e67-133">Repair .NET Framework 3.0 after .NET Framework 3.5 Installation</span></span>

 <span data-ttu-id="c9e67-134">.NET Framework 3,5 yükledikten sonra .NET Framework 3,0 ' ı onarırsanız, *machine.config* .NET Framework 3,5 tarafından tanıtılan yapılandırma öğeleri kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c9e67-134">If you do a repair of .NET Framework 3.0 after you installed .NET Framework 3.5, configuration elements introduced by .NET Framework 3.5 in *machine.config* are removed.</span></span> <span data-ttu-id="c9e67-135">Ancak, *web.config* dosyası bozulmadan kalır.</span><span class="sxs-lookup"><span data-stu-id="c9e67-135">However, the *web.config* file remains intact.</span></span> <span data-ttu-id="c9e67-136">Geçici çözüm, bu ARP aracılığıyla .NET Framework 3,5 ' i onarmak veya anahtarla [Iş akışı hizmeti kayıt aracı 'nı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) kullanmaktır `/c` .</span><span class="sxs-lookup"><span data-stu-id="c9e67-136">The workaround is to repair .NET Framework 3.5 after this via ARP, or use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch.</span></span>  
  
 <span data-ttu-id="c9e67-137">[Workflow Service kayıt aracı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\Framework\v3.5\ veya%windir%\Microsoft.NET\Framework64\v3.5\ adresinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="c9e67-137">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a><span data-ttu-id="c9e67-138">.NET Framework 3,5 yükledikten sonra IIS 'Yi WCF/WF Webhost için düzgün şekilde yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9e67-138">Configure IIS Properly for WCF/WF Webhost after Installing .NET Framework 3.5</span></span>  
 <span data-ttu-id="c9e67-139">.NET Framework 3,5 yüklemesi, WCF ile ilgili ek IIS yapılandırma ayarlarını yapılandıramazsa, yükleme günlüğünde bir hata kaydeder ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="c9e67-139">When .NET Framework 3.5 installation fails to configure additional WCF-related IIS configuration settings, it logs an error in the installation log and continues.</span></span> <span data-ttu-id="c9e67-140">Gerekli yapılandırma ayarları eksik olduğundan, WorkflowServices uygulamalarını çalıştırma girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c9e67-140">Any attempt to run WorkflowServices applications will fail, since the required configuration settings are missing.</span></span> <span data-ttu-id="c9e67-141">Örneğin, xoml veya Rules hizmeti yüklenirken hata oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="c9e67-141">For example, loading xoml or rules service can fail.</span></span>  
  
 <span data-ttu-id="c9e67-142">Bu sorunu geçici olarak çözmek için, [Iş akışı hizmeti kayıt aracı 'nı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) `/c` makinede IIS komut dosyası eşlemelerini doğru şekilde yapılandırmak için anahtarla kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9e67-142">To workaround this problem, use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch to properly configure IIS script maps on the machine.</span></span> <span data-ttu-id="c9e67-143">[Workflow Service kayıt aracı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\Framework\v3.5\ veya%windir%\Microsoft.NET\Framework64\v3.5\ adresinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="c9e67-143">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule"></a><span data-ttu-id="c9e67-144">' System. ServiceModel. Activation. HttpModule ' türü yüklenemedi</span><span class="sxs-lookup"><span data-stu-id="c9e67-144">Could not load type 'System.ServiceModel.Activation.HttpModule'</span></span>

<span data-ttu-id="c9e67-145">**' System. ServiceModel. Activation. HttpModule ' türü, ' System. ServiceModel, Version 3.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089 ' derlemesinden yüklenemedi**</span><span class="sxs-lookup"><span data-stu-id="c9e67-145">**Could not load type 'System.ServiceModel.Activation.HttpModule' from assembly 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'**</span></span>

 <span data-ttu-id="c9e67-146">.NET Framework 4 yüklüyse ve WCF HTTP etkinleştirmesi etkinse bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="c9e67-146">This error occurs if .NET Framework 4 is installed and then WCF HTTP Activation is enabled.</span></span> <span data-ttu-id="c9e67-147">Sorunu çözmek için, Visual Studio Geliştirici Komut İstemi içinden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c9e67-147">To resolve the issue, run the following command from inside the Developer Command Prompt for Visual Studio:</span></span>  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9e67-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9e67-148">See also</span></span>

- [<span data-ttu-id="c9e67-149">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c9e67-149">Set-Up Instructions</span></span>](./samples/set-up-instructions.md)
