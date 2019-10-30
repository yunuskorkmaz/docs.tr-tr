---
title: 'Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 98fb57abfff985ab96cb5139f15ae4c29c986a18
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040617"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="b9630-102">Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="b9630-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="b9630-103">Aşağıdaki kod örneği, IPv6 desteğinin etkinleştirilmesi için *Machine. config*bilgisayar yapılandırma dosyasının nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b9630-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="b9630-104">*Machine. config* dosyası, Windows 'un yüklendiği dizindeki *%windir%\Microsoft.NET\Framework* klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="b9630-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="b9630-105">Bilgisayarda yüklü .NET Framework her sürümü için *%windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *Machine. config* dosyası bulunur (örneğin, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\ Machine. config*).</span><span class="sxs-lookup"><span data-stu-id="b9630-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="b9630-106">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b9630-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="b9630-107">.NET Framework sürüm 1,1 ve önceki sürümlerde **IPv6 etkin** yapılandırma anahtarının değeri, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfının üyelerinin IPv6 adresleri döndürmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b9630-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="b9630-108">.NET Framework sürüm 2,0 ve üzeri için, Windows IPv6 'yı destekliyorsa, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfının tüm üyeleri (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi) bir sınırlamaya sahip IPv6 adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b9630-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="b9630-109"><xref:System.Net.Dns?displayProperty=nameWithType> sınıfının kullanılmayan üyeleri (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) yapılandırma dosyasındaki değeri okur ve tanır.</span><span class="sxs-lookup"><span data-stu-id="b9630-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9630-110">.NET Framework sürüm 2,0 ve üzeri için IPv6 varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="b9630-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="b9630-111">.NET Framework sürüm 1,1 ve önceki sürümlerde IPv6 varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b9630-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9630-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9630-112">Example</span></span>  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9630-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9630-113">See also</span></span>

- [<span data-ttu-id="b9630-114">IPv6 Adresleme</span><span class="sxs-lookup"><span data-stu-id="b9630-114">IPv6 Addressing</span></span>](ipv6-addressing.md)
- [<span data-ttu-id="b9630-115">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b9630-115">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="b9630-116">\<IPv6 > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b9630-116">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
