---
title: 'Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme'
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: bab8ad63641bd62b957d1aeb71a0d0f8a30df253
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642600"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="581a7-102">Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="581a7-102">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>
<span data-ttu-id="581a7-103">Aşağıdaki kod örneği bilgisayar yapılandırma dosyasının nasıl değiştirileceğini gösterir *machine.config*, IPv6 desteğini etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="581a7-103">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="581a7-104">*Machine.config* dosyasının depolandığı *%Windir%\Microsoft.NET\Framework* dizinde Windows yüklendiği klasör.</span><span class="sxs-lookup"><span data-stu-id="581a7-104">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="581a7-105">Ayrı bir yoktur *machine.config* altındaki klasörler dosyasında *%Windir%\Microsoft.NET\Framework* bilgisayarda yüklü .NET Framework'ün her sürümü için (örneğin, *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="581a7-105">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="581a7-106">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="581a7-106">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="581a7-107">.NET Framework sürüm 1.1 ve önceki değerini **IPv6 etkin** yapılandırma anahtarı belirtir olup olmadığını üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> sınıf, IPv6 adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="581a7-107">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="581a7-108">.NET Framework sürüm 2.0 ve üzeri, Windows IPv6, ardından tüm üyelerinin destekliyorsa <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi), tek bir kısıtlama olmaksızın IPv6 adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="581a7-108">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="581a7-109">Üyeleri geçersiz <xref:System.Net.Dns?displayProperty=nameWithType> sınıfı (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) okuyun ve yapılandırma dosyasında değer tanınamıyor.</span><span class="sxs-lookup"><span data-stu-id="581a7-109">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="581a7-110">.NET Framework sürüm 2.0 ve sonraki sürümleri için IPv6, varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="581a7-110">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="581a7-111">.NET Framework sürüm 1.1 ve önceki sürümler için IPv6, varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="581a7-111">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="581a7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="581a7-112">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="581a7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="581a7-113">See also</span></span>

- [<span data-ttu-id="581a7-114">IPv6 Adresleme</span><span class="sxs-lookup"><span data-stu-id="581a7-114">IPv6 Addressing</span></span>](../../../docs/framework/network-programming/ipv6-addressing.md)
- [<span data-ttu-id="581a7-115">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="581a7-115">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="581a7-116">\<IPv6 > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="581a7-116">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
