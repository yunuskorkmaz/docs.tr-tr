---
description: 'Daha fazla bilgi edinin: WCF ve uluslararası etki alanı adları'
title: WCF ve Uluslararası Hale Getirilmiş Etki Alanı Adları
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: e7e1ad999d7de749b4f8cf4b3efd823befffba43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755999"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="33eae-103">WCF ve Uluslararası Hale Getirilmiş Etki Alanı Adları</span><span class="sxs-lookup"><span data-stu-id="33eae-103">WCF and Internationalized Domain Names</span></span>

<span data-ttu-id="33eae-104">Uluslararası etki alanı adlarına (ıDN) sahip WCF hizmetlerine izin vermek için destek eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="33eae-104">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="33eae-105">Uluslararası bir etki alanı adı ASCII olmayan karakterler içeren bir etki alanı adıdır.</span><span class="sxs-lookup"><span data-stu-id="33eae-105">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="33eae-106">Bu destek, hem ıDN adı ile bir WCF hizmetini hem de bir ıDN adıyla bir Web hizmetiyle konuşmak üzere bir WCF istemcisini barındırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="33eae-106">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="33eae-107">System. Uri ve ıDN</span><span class="sxs-lookup"><span data-stu-id="33eae-107">System.Uri and IDN</span></span>  

 <span data-ttu-id="33eae-108"><xref:System.Uri> iki özelliğe sahiptir <xref:System.Uri.Host%2A> <xref:System.Uri.DnsSafeHost%2A> .</span><span class="sxs-lookup"><span data-stu-id="33eae-108"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="33eae-109">Bu özellikler, ıDN yapılandırma ayarlarına bağlı olarak Unicode veya Punyıcode değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="33eae-109">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="33eae-110">IDN, bir uygulamanın yapılandırma dosyasında aşağıdaki XML kullanılarak etkinleştirildi</span><span class="sxs-lookup"><span data-stu-id="33eae-110">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="33eae-111">\<idn>Öğesi, aşağıdaki değerlerden birine ayarlanbilen enabled özniteliğini içerir:</span><span class="sxs-lookup"><span data-stu-id="33eae-111">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1. <span data-ttu-id="33eae-112">Seçim</span><span class="sxs-lookup"><span data-stu-id="33eae-112">"None"</span></span>  
  
2. <span data-ttu-id="33eae-113">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="33eae-113">"AllExceptIntranet"</span></span>  
  
3. <span data-ttu-id="33eae-114">Bütün</span><span class="sxs-lookup"><span data-stu-id="33eae-114">"All"</span></span>  
  
 <span data-ttu-id="33eae-115">IDN ayarı "none" olarak ayarlandığında, Uri. Host veya Uri. DnsSafeHost tarafından hiçbir dönüştürme yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="33eae-115">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="33eae-116">IDN ayarı "All", URI olarak ayarlandığında. Ana bilgisayar Unicode ve URI kalır. DnsSafeHost, Punyıcode 'a dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="33eae-116">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="33eae-117">IDN ayarı "AllExceptIntranet" olarak ayarlandığında URI. DnsSafeHost Internet adresleri için zayıf koda dönüştürülür ve intranet adresleri için Unicode olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="33eae-117">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="33eae-118">Bu ayar, doğru DNS ad çözümlemesi için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="33eae-118">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="33eae-119">Not Bu ayarın, Windows 8 ve daha yeni sürümler için yapılandırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="33eae-119">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="33eae-120">Punyıcode kullanarak bir adresi asla sabit bir şekilde kodmalısınız.</span><span class="sxs-lookup"><span data-stu-id="33eae-120">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="33eae-121">WCF, uyguladığınız yapılandırma ayarlarına bağlı olarak bunu sizin için dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="33eae-121">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="33eae-122">applicationHost.exe.config için Unicode karakterler eklerken, dosyayı UTF-8 kodlamasını kullanarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="33eae-122">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33eae-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33eae-123">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
