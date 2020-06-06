---
title: <idn> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698168"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="65bc3-102">\<idn> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="65bc3-102">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="65bc3-103">Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="65bc3-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**  
  
## <a name="syntax"></a><span data-ttu-id="65bc3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65bc3-104">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65bc3-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="65bc3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="65bc3-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="65bc3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65bc3-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="65bc3-107">Attributes</span></span>  

|<span data-ttu-id="65bc3-108">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="65bc3-108">**Element**</span></span>|<span data-ttu-id="65bc3-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="65bc3-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="65bc3-110">Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir varsayılan değer None ' dır.</span><span class="sxs-lookup"><span data-stu-id="65bc3-110">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="65bc3-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="65bc3-111">Child elements</span></span>

<span data-ttu-id="65bc3-112">Yok</span><span class="sxs-lookup"><span data-stu-id="65bc3-112">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="65bc3-113">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="65bc3-113">Parent elements</span></span>

|<span data-ttu-id="65bc3-114">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="65bc3-114">**Element**</span></span>|<span data-ttu-id="65bc3-115">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="65bc3-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="65bc3-116">kullanılmamışsa</span><span class="sxs-lookup"><span data-stu-id="65bc3-116">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="65bc3-117">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="65bc3-117">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="65bc3-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65bc3-118">Remarks</span></span>

<span data-ttu-id="65bc3-119">Mevcut <xref:System.Uri> sınıf .NET Framework 3,5 ' de genişletildi.</span><span class="sxs-lookup"><span data-stu-id="65bc3-119">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="65bc3-120">3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) desteğiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="65bc3-120">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="65bc3-121">IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="65bc3-121">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="65bc3-122">Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="65bc3-122">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="65bc3-123">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="65bc3-123">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="65bc3-124">Aşağıdaki satırı .NET Framework 2,0 dizinindeki Machine. config dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="65bc3-124">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="65bc3-125">Uluslararası etki alanı adı (ıDN) ayrıştırmayı etki alanı adına uygulanıp uygulanmayacağını ve IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="65bc3-125">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="65bc3-126">Bu, Machine. config veya App. config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="65bc3-126">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="65bc3-127">Kullanılan DNS sunucularına bağlı olarak ıDN için üç olası değer vardır:</span><span class="sxs-lookup"><span data-stu-id="65bc3-127">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="65bc3-128">IDN etkin = tümü</span><span class="sxs-lookup"><span data-stu-id="65bc3-128">idn enabled = All</span></span>  

     <span data-ttu-id="65bc3-129">Bu değer, herhangi bir Unicode etki alanı adını, zayıf kod eşdeğerlerine (ıDN adları) dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="65bc3-129">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="65bc3-130">IDN etkin = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="65bc3-130">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="65bc3-131">Bu değer, yerel Intranette bulunmayan tüm Unicode etki alanı adlarını, Punyıcode eşdeğerlerini (ıDN adları) kullanacak şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="65bc3-131">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="65bc3-132">Bu durumda, yerel Intranetteki uluslararası adları işlemek için, Intranet için kullanılan DNS sunucularının Unicode ad çözümlemesini desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="65bc3-132">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="65bc3-133">IDN etkin = yok</span><span class="sxs-lookup"><span data-stu-id="65bc3-133">idn enabled = None</span></span>

     <span data-ttu-id="65bc3-134">Bu değer, herhangi bir Unicode etki alanı adını Punyıcode kullanacak şekilde dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="65bc3-134">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="65bc3-135">Bu, .NET Framework 2,0 davranışıyla tutarlı olan varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="65bc3-135">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="65bc3-136">IDN 'yi etkinleştirmek, bir etki alanı adındaki tüm Unicode etiketlerini atlama kodu eşdeğerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="65bc3-136">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="65bc3-137">Puni Code adları yalnızca ASCII karakterleri içerir ve her zaman xn--önekiyle başlar.</span><span class="sxs-lookup"><span data-stu-id="65bc3-137">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="65bc3-138">Bunun nedeni, DNS sunucularının çoğu yalnızca ASCII karakterlerini desteklediği için Internet 'teki mevcut DNS sunucularını desteklemedir (bkz. RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="65bc3-138">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="65bc3-139">Yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="65bc3-139">Configuration files</span></span>

<span data-ttu-id="65bc3-140">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="65bc3-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="65bc3-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="65bc3-141">Example</span></span>

<span data-ttu-id="65bc3-142">Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="65bc3-142">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="65bc3-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65bc3-143">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="65bc3-144">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="65bc3-144">Network Settings Schema</span></span>](index.md)
