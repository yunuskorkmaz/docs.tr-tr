---
title: "Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayarı yapılandırma dosyasını değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 696aeb619f14a5ebe9a760cbd78a0d0fa876edc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="110c2-102">Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayarı yapılandırma dosyasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="110c2-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="110c2-103">Aşağıdaki kod örneğinde bilgisayar yapılandırma dosyasının nasıl değiştirileceğini gösterir *machine.config*, IPv6 desteğini etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="110c2-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="110c2-104">*Machine.config* dosya depolanır *%Windir%\Microsoft.NET\Framework* Windows yüklendiği klasörü dizininde.</span><span class="sxs-lookup"><span data-stu-id="110c2-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="110c2-105">Ayrı bir yoktur *machine.config* altındaki klasörler dosyasında *%Windir%\Microsoft.NET\Framework* her bilgisayarda yüklü .NET Framework sürümü için (örneğin, *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="110c2-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="110c2-106">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="110c2-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="110c2-107">.NET Framework sürüm 1.1 ve önceki değeri için **etkin IPv6** yapılandırma anahtarı belirtir olup olmadığını üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı IPv6 adresleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="110c2-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="110c2-108">.NET Framework sürüm 2.0 ve daha sonra Windows IPv6 sonra tüm üyeleri destekliyorsa için <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi), IPv6 adresleriyle bir sınırlama döndürür.</span><span class="sxs-lookup"><span data-stu-id="110c2-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="110c2-109">Kullanımdan kalktı üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) okuma ve yapılandırma dosyasındaki değer tanınamıyor.</span><span class="sxs-lookup"><span data-stu-id="110c2-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="110c2-110">.NET Framework sürüm 2.0 ve sonraki sürümleri için IPv6 varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="110c2-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="110c2-111">.NET Framework sürüm 1.1 ve önceki sürümler için IPv6 varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="110c2-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="110c2-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="110c2-112">Example</span></span>  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="110c2-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="110c2-113">See Also</span></span>  
 [<span data-ttu-id="110c2-114">IPv6 adresi</span><span class="sxs-lookup"><span data-stu-id="110c2-114">IPv6 Addressing</span></span>](../../../docs/framework/network-programming/ipv6-addressing.md)  
 [<span data-ttu-id="110c2-115">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="110c2-115">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="110c2-116">\<IPv6 > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="110c2-116">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
