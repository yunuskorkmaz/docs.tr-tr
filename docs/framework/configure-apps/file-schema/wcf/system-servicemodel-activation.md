---
title: <system.serviceModel.activation>
ms.date: 03/30/2017
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
ms.openlocfilehash: e00bbad452398e7f8f4f50208da572986391fc9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399472"
---
# \<system.serviceModel.activation>
<span data-ttu-id="ca34c-102">Bu yapılandırma bölümü, SMSvcHost. exe aracı için yapılandırma ayarlarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ca34c-102">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="ca34c-103">Yapılandırma öğeleri SMSvcHost. exe. config dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca34c-103">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="ca34c-104">Özellikle, yapılandırılması gereken tüm makine genelinde ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ca34c-104">Specifically, it includes all machine-wide settings that must be configured.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel.activation>**  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="ca34c-105">Örnek yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="ca34c-105">Sample Configuration File</span></span>  
 <span data-ttu-id="ca34c-106">Aşağıda, SMSvcHost. exe dinleyici işlemi tarafından kullanılan örnek bir yapılandırma dosyası (SMSvcHost. exe. config) verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ca34c-106">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
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
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
    <diagnostics performanceCountersEnabled="true" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="ca34c-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca34c-107">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration>
