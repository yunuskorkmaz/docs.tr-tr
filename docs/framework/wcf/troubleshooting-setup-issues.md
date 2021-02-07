---
description: 'Hakkında daha fazla bilgi edinin: Kurulum sorunlarını giderme'
title: Kurulum Sorunlarını Giderme
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 8beb404040c15ade8f435772fe1b947eef766702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703477"
---
# <a name="troubleshoot-setup-issues"></a><span data-ttu-id="8b222-103">Kurulum sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="8b222-103">Troubleshoot setup issues</span></span>

<span data-ttu-id="8b222-104">Bu makalede Windows Communication Foundation (WCF) kurulum sorunlarını nasıl giderebileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8b222-104">This article describes how to troubleshoot Windows Communication Foundation (WCF) setup issues.</span></span>  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a><span data-ttu-id="8b222-105">Bazı Windows Communication Foundation kayıt defteri anahtarları, .NET Framework 3,0 üzerinde MSI onarım Işlemi gerçekleştirerek onarılmıyor</span><span class="sxs-lookup"><span data-stu-id="8b222-105">Some Windows Communication Foundation Registry Keys are not Repaired by Performing an MSI Repair Operation on the .NET Framework 3.0</span></span>  

 <span data-ttu-id="8b222-106">Aşağıdaki kayıt defteri anahtarlarından birini silerseniz:</span><span class="sxs-lookup"><span data-stu-id="8b222-106">If you delete any of the following registry keys:</span></span>  
  
- <span data-ttu-id="8b222-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="8b222-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span></span>  
  
- <span data-ttu-id="8b222-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="8b222-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span></span>  
  
- <span data-ttu-id="8b222-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="8b222-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span></span>  
  
- <span data-ttu-id="8b222-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="8b222-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span></span>  
  
- <span data-ttu-id="8b222-111">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="8b222-111">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span></span>  
  
 <span data-ttu-id="8b222-112">**Denetim Masası**'Ndaki **Program Ekle/kaldır** uygulamasından başlatılan .NET Framework 3,0 yükleyicisini kullanarak Onar 'ı çalıştırırsanız anahtarlar yeniden oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="8b222-112">The keys are not re-created if you run repair by using the .NET Framework 3.0 installer launched from the **Add/Remove Programs** applet in **Control Panel**.</span></span> <span data-ttu-id="8b222-113">Bu anahtarları doğru bir şekilde yeniden oluşturmak için, Kullanıcı .NET Framework 3,0 ' i kaldırmalı ve yeniden yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8b222-113">To recreate these keys correctly, the user must uninstall and reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-wmi-provider"></a><span data-ttu-id="8b222-114">WMI hizmeti bozulması, WMI sağlayıcısının yüklenmesini engelliyor</span><span class="sxs-lookup"><span data-stu-id="8b222-114">WMI Service Corruption Blocks Installation of the WMI provider</span></span>

 <span data-ttu-id="8b222-115">WMI hizmeti bozulması, .NET Framework 3,0 paketini yüklerken Windows Communication Foundation WMI sağlayıcısının yüklenmesini engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8b222-115">WMI Service Corruption may block the installation of the Windows Communication Foundation WMI provider when installing the .NET Framework 3.0 package.</span></span> <span data-ttu-id="8b222-116">Yükleme sırasında Windows Communication Foundation yükleyicisi, *mofcomp.exe* BILEŞENINI kullanarak WCF *. mof* dosyasını kaydedemiyor.</span><span class="sxs-lookup"><span data-stu-id="8b222-116">During installation, the Windows Communication Foundation installer is unable to register the WCF *.mof* file using the *mofcomp.exe* component.</span></span> <span data-ttu-id="8b222-117">Belirtilerin listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b222-117">The following is a list of symptoms:</span></span>  
  
1. <span data-ttu-id="8b222-118">.NET Framework 3,0 yüklemesi başarıyla tamamlandı, ancak WCF WMI sağlayıcısı kayıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="8b222-118">.NET Framework 3.0 installation completes successfully, but the WCF WMI provider is not registered.</span></span>  
  
2. <span data-ttu-id="8b222-119">Uygulama olay günlüğünde, WCF için WMI sağlayıcısını kaydettirme veya mofcomp.exe çalıştırma sorunlarına başvuran bir hata olayı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8b222-119">An error event appears in the application event log that references problems registering the WMI provider for WCF, or running mofcomp.exe.</span></span>  
  
3. <span data-ttu-id="8b222-120">Kullanıcının% Temp% dizininde dd_wcf_retCA \* adlı kurulum günlük dosyası, WCF WMI sağlayıcısını kaydetme hatasına yönelik başvurular içeriyor.</span><span class="sxs-lookup"><span data-stu-id="8b222-120">The setup log file named dd_wcf_retCA\* in the user's %temp% directory contains references to failure to register the WCF WMI provider.</span></span>  
  
4. <span data-ttu-id="8b222-121">Olay günlüğünde veya kurulum izleme günlük dosyasında aşağıdakiler gibi bir özel durum listelenebilir:</span><span class="sxs-lookup"><span data-stu-id="8b222-121">An exception such as one the following may be listed in the event log or setup trace log file:</span></span>  
  
     <span data-ttu-id="8b222-122">ServiceModelReg [11:09:59:046]: System. ApplicationException: beklenmeyen sonuç 3, "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof" ile E:\WINDOWS\system32\wbem\mofcomp.exe yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="8b222-122">ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"</span></span>  
  
     <span data-ttu-id="8b222-123">veya:</span><span class="sxs-lookup"><span data-stu-id="8b222-123">or:</span></span>  
  
     <span data-ttu-id="8b222-124">ServiceModelReg [07:19:33:843]: System. TypeInitializationException: ' System. Management. ManagementPath ' için tür başlatıcısı özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="8b222-124">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception.</span></span> <span data-ttu-id="8b222-125">---> System. Runtime. InteropServices. COMException (0x80040154): CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} olan bileşen için COM sınıfı fabrikasını alma işlemi şu hata nedeniyle başarısız oldu: 80040154.</span><span class="sxs-lookup"><span data-stu-id="8b222-125">---> System.Runtime.InteropServices.COMException (0x80040154): Retrieving the COM class factory for component with CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} failed due to the following error: 80040154.</span></span>  
  
     <span data-ttu-id="8b222-126">veya:</span><span class="sxs-lookup"><span data-stu-id="8b222-126">or:</span></span>  
  
     <span data-ttu-id="8b222-127">ServiceModelReg [07:19:32:750]: System. ıO. FileNotFoundException: ' C:\WINDOWS\system32\wbem\mofcomp.exe ' dosyası veya bütünleştirilmiş kodu veya bağımlılıklarından biri yüklenemedi.</span><span class="sxs-lookup"><span data-stu-id="8b222-127">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies.</span></span> <span data-ttu-id="8b222-128">Sistem belirtilen dosyayı bulamıyor.</span><span class="sxs-lookup"><span data-stu-id="8b222-128">The system cannot find the file specified.</span></span>  
  
     <span data-ttu-id="8b222-129">Dosya adı: ' C:\WINDOWS\system32\wbem\mofcomp.exe</span><span class="sxs-lookup"><span data-stu-id="8b222-129">File name: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span></span>  
  
 <span data-ttu-id="8b222-130">Daha önce açıklanan sorunu çözmek için aşağıdaki adımlar izlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b222-130">The following steps must be followed to resolve the problem described previously.</span></span>  
  
1. <span data-ttu-id="8b222-131">WMI hizmetini onarmak için WMI Diagnosis Utility çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8b222-131">Run the WMI Diagnosis Utility to repair the WMI service.</span></span> <span data-ttu-id="8b222-132">Bu aracı kullanma hakkında daha fazla bilgi için bkz. [WMI diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span><span class="sxs-lookup"><span data-stu-id="8b222-132">For more information about using this tool, see [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span></span>  
  
 <span data-ttu-id="8b222-133">**Denetim Masası**'Nda bulunan **Program Ekle/kaldır** uygulamasını kullanarak .NET Framework 3,0 yüklemesini onarın veya .NET Framework 3,0 ' i kaldırın/yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="8b222-133">Repair the .NET Framework 3.0 installation by using the **Add/Remove Programs** applet located in **Control Panel**, or uninstall/reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="repair-net-framework-30-after-net-framework-35-installation"></a><span data-ttu-id="8b222-134">.NET Framework 3,5 yüklemesinden sonra .NET Framework 3,0 ' i Onar</span><span class="sxs-lookup"><span data-stu-id="8b222-134">Repair .NET Framework 3.0 after .NET Framework 3.5 Installation</span></span>

 <span data-ttu-id="8b222-135">.NET Framework 3,5 yükledikten sonra .NET Framework 3,0 ' ı onarırsanız, *machine.config* .NET Framework 3,5 tarafından tanıtılan yapılandırma öğeleri kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="8b222-135">If you do a repair of .NET Framework 3.0 after you installed .NET Framework 3.5, configuration elements introduced by .NET Framework 3.5 in *machine.config* are removed.</span></span> <span data-ttu-id="8b222-136">Ancak, *web.config* dosyası bozulmadan kalır.</span><span class="sxs-lookup"><span data-stu-id="8b222-136">However, the *web.config* file remains intact.</span></span> <span data-ttu-id="8b222-137">Geçici çözüm, bu ARP aracılığıyla .NET Framework 3,5 ' i onarmak veya anahtarla [Iş akışı hizmeti kayıt aracı 'nı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) kullanmaktır `/c` .</span><span class="sxs-lookup"><span data-stu-id="8b222-137">The workaround is to repair .NET Framework 3.5 after this via ARP, or use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch.</span></span>  
  
 <span data-ttu-id="8b222-138">[Workflow Service kayıt aracı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\Framework\v3.5\ veya%windir%\Microsoft.NET\Framework64\v3.5\ adresinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="8b222-138">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a><span data-ttu-id="8b222-139">.NET Framework 3,5 yükledikten sonra IIS 'Yi WCF/WF Webhost için düzgün şekilde yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8b222-139">Configure IIS Properly for WCF/WF Webhost after Installing .NET Framework 3.5</span></span>  

 <span data-ttu-id="8b222-140">.NET Framework 3,5 yüklemesi, WCF ile ilgili ek IIS yapılandırma ayarlarını yapılandıramazsa, yükleme günlüğünde bir hata kaydeder ve devam eder.</span><span class="sxs-lookup"><span data-stu-id="8b222-140">When .NET Framework 3.5 installation fails to configure additional WCF-related IIS configuration settings, it logs an error in the installation log and continues.</span></span> <span data-ttu-id="8b222-141">Gerekli yapılandırma ayarları eksik olduğundan, WorkflowServices uygulamalarını çalıştırma girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8b222-141">Any attempt to run WorkflowServices applications will fail, since the required configuration settings are missing.</span></span> <span data-ttu-id="8b222-142">Örneğin, xoml veya Rules hizmeti yüklenirken hata oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="8b222-142">For example, loading xoml or rules service can fail.</span></span>  
  
 <span data-ttu-id="8b222-143">Bu sorunu geçici olarak çözmek için, [Iş akışı hizmeti kayıt aracı 'nı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) `/c` makinede IIS komut dosyası eşlemelerini doğru şekilde yapılandırmak için anahtarla kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b222-143">To workaround this problem, use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch to properly configure IIS script maps on the machine.</span></span> <span data-ttu-id="8b222-144">[Workflow Service kayıt aracı (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) %windir%\Microsoft.NET\Framework\v3.5\ veya%windir%\Microsoft.NET\Framework64\v3.5\ adresinde bulunabilir</span><span class="sxs-lookup"><span data-stu-id="8b222-144">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule"></a><span data-ttu-id="8b222-145">' System. ServiceModel. Activation. HttpModule ' türü yüklenemedi</span><span class="sxs-lookup"><span data-stu-id="8b222-145">Could not load type 'System.ServiceModel.Activation.HttpModule'</span></span>

<span data-ttu-id="8b222-146">**' System. ServiceModel. Activation. HttpModule ' türü, ' System. ServiceModel, Version 3.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089 ' derlemesinden yüklenemedi**</span><span class="sxs-lookup"><span data-stu-id="8b222-146">**Could not load type 'System.ServiceModel.Activation.HttpModule' from assembly 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'**</span></span>

 <span data-ttu-id="8b222-147">.NET Framework 4 yüklüyse ve WCF HTTP etkinleştirmesi etkinse bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="8b222-147">This error occurs if .NET Framework 4 is installed and then WCF HTTP Activation is enabled.</span></span> <span data-ttu-id="8b222-148">Sorunu çözmek için, Visual Studio Geliştirici Komut İstemi içinden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="8b222-148">To resolve the issue, run the following command from inside the Developer Command Prompt for Visual Studio:</span></span>  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b222-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b222-149">See also</span></span>

- [<span data-ttu-id="8b222-150">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8b222-150">Set-Up Instructions</span></span>](./samples/set-up-instructions.md)
