---
title: 'Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 73408afe9fcb35daa898c08b087a3411a6cb342b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180800"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="e66a6-102">Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e66a6-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="e66a6-103">Aşağıdaki kod örneği, IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyası *machine.config'in*nasıl değiştirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e66a6-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="e66a6-104">*machine.config* dosyası, Windows'un yüklendiği dizinde *%Windir%\Microsoft.NET\Framework* klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="e66a6-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="e66a6-105">Bilgisayarda yüklü olan .NET Framework'ün her sürümü için *%Windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *machine.config* dosyası bulunmaktadır (örneğin, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config).*</span><span class="sxs-lookup"><span data-stu-id="e66a6-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="e66a6-106">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="e66a6-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="e66a6-107">.NET Framework sürüm 1.1 ve daha önceki sürümiçin, **ipv6 etkinleştirilmiş** <xref:System.Net.Dns?displayProperty=nameWithType> yapılandırma anahtarının değeri, sınıf üyelerinin IPv6 adreslerini döndürüp döndürmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e66a6-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="e66a6-108">.NET Framework sürüm 2.0 ve sonrası için, Windows IPv6'yı destekliyorsa, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın tüm üyeleri (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntem), IPv6 adreslerini tek bir sınırlamayla döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="e66a6-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="e66a6-109"><xref:System.Net.Dns?displayProperty=nameWithType> Sınıfın eski üyeleri (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntem) yapılandırma dosyasındaki değeri okur ve tanır.</span><span class="sxs-lookup"><span data-stu-id="e66a6-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e66a6-110">.NET Framework sürüm 2.0 ve sonrası için, IPv6 varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e66a6-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="e66a6-111">.NET Framework sürüm 1.1 ve daha önceki sürümiçin, IPv6 varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="e66a6-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e66a6-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e66a6-112">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e66a6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e66a6-113">See also</span></span>

- [<span data-ttu-id="e66a6-114">IPv6 Adresleme</span><span class="sxs-lookup"><span data-stu-id="e66a6-114">IPv6 Addressing</span></span>](ipv6-addressing.md)
- [<span data-ttu-id="e66a6-115">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e66a6-115">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="e66a6-116">\<ipv6> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="e66a6-116">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
