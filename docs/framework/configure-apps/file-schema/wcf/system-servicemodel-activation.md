---
title: '&lt;system.serviceModel.activation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f15466e5ae0421f400d80f66370cb60f75c83990
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemservicemodelactivationgt"></a><span data-ttu-id="61182-102">&lt;system.serviceModel.activation&gt;</span><span class="sxs-lookup"><span data-stu-id="61182-102">&lt;system.serviceModel.activation&gt;</span></span>
<span data-ttu-id="61182-103">Bu yapılandırma bölümü SMSvcHost.exe Aracı'nı yapılandırma ayarlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="61182-103">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="61182-104">Yapılandırma öğelerini erişimi dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="61182-104">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="61182-105">Özellikle yapılandırılması gereken tüm makine genelinde ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="61182-105">Specifically, it includes all machine-wide settings that must be configured.</span></span>  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="61182-106">Örnek yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="61182-106">Sample Configuration File</span></span>  
 <span data-ttu-id="61182-107">Dinleyici işlem SMSvcHost.exe tarafından kullanılan örnek bir yapılandırma dosyası (erişimi) verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="61182-107">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false" />  
   </runtime>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="10"  
          maxPendingAccepts="2"  
          maxPendingConnections="100"  
          receiveTimeout="00:00:10"  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Network Service account -->  
            <add securityIdentifier="S-1-5-20"/>   
             <!-- Administrators account -->  
            <add securityIdentifier="S-1-5-32-544" />   
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
       <net.pipe maxConnectionsPendingDispatch="100"  
          maxPendingAccepts="2"  
          receiveTimeout="00:00:10">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Network Service account -->  
            <add securityIdentifier="S-1-5-20"/>   
             <!-- Administrators account -->  
            <add securityIdentifier="S-1-5-32-544" />   
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
       <diagnostics performanceCountersEnabled="true" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61182-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61182-108">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration>
