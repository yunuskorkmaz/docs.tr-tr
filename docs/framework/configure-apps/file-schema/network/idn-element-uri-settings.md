---
description: 'Daha fazla bilgi edinin: <idn> öğesi (URI ayarları)'
title: <idn> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: a53afd59b713a804d5b969521f468000dbbad6e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802482"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="6848b-103">\<idn> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6848b-103">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="6848b-104">Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6848b-104">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**  
  
## <a name="syntax"></a><span data-ttu-id="6848b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6848b-105">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6848b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6848b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6848b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6848b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6848b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6848b-108">Attributes</span></span>  

|<span data-ttu-id="6848b-109">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6848b-109">**Element**</span></span>|<span data-ttu-id="6848b-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6848b-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="6848b-111">Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir varsayılan değer None ' dır.</span><span class="sxs-lookup"><span data-stu-id="6848b-111">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="6848b-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6848b-112">Child elements</span></span>

<span data-ttu-id="6848b-113">Yok</span><span class="sxs-lookup"><span data-stu-id="6848b-113">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="6848b-114">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6848b-114">Parent elements</span></span>

|<span data-ttu-id="6848b-115">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6848b-115">**Element**</span></span>|<span data-ttu-id="6848b-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6848b-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6848b-117">kullanılmamışsa</span><span class="sxs-lookup"><span data-stu-id="6848b-117">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="6848b-118">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="6848b-118">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="6848b-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6848b-119">Remarks</span></span>

<span data-ttu-id="6848b-120">Mevcut <xref:System.Uri> sınıf .NET Framework 3,5 ' de genişletildi.</span><span class="sxs-lookup"><span data-stu-id="6848b-120">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="6848b-121">3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) desteğiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6848b-121">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="6848b-122">IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="6848b-122">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="6848b-123">Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="6848b-123">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="6848b-124">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="6848b-124">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="6848b-125">Aşağıdaki satırı .NET Framework 2,0 dizinindeki machine.config dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6848b-125">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="6848b-126">Uluslararası etki alanı adı (ıDN) ayrıştırmayı etki alanı adına uygulanıp uygulanmayacağını ve IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="6848b-126">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="6848b-127">Bu, machine.config veya app.config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="6848b-127">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="6848b-128">Kullanılan DNS sunucularına bağlı olarak ıDN için üç olası değer vardır:</span><span class="sxs-lookup"><span data-stu-id="6848b-128">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="6848b-129">IDN etkin = tümü</span><span class="sxs-lookup"><span data-stu-id="6848b-129">idn enabled = All</span></span>  

     <span data-ttu-id="6848b-130">Bu değer, herhangi bir Unicode etki alanı adını, zayıf kod eşdeğerlerine (ıDN adları) dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6848b-130">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="6848b-131">IDN etkin = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="6848b-131">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="6848b-132">Bu değer, yerel Intranette bulunmayan tüm Unicode etki alanı adlarını, Punyıcode eşdeğerlerini (ıDN adları) kullanacak şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6848b-132">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="6848b-133">Bu durumda, yerel Intranetteki uluslararası adları işlemek için, Intranet için kullanılan DNS sunucularının Unicode ad çözümlemesini desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6848b-133">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="6848b-134">IDN etkin = yok</span><span class="sxs-lookup"><span data-stu-id="6848b-134">idn enabled = None</span></span>

     <span data-ttu-id="6848b-135">Bu değer, herhangi bir Unicode etki alanı adını Punyıcode kullanacak şekilde dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="6848b-135">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="6848b-136">Bu, .NET Framework 2,0 davranışıyla tutarlı olan varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6848b-136">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="6848b-137">IDN 'yi etkinleştirmek, bir etki alanı adındaki tüm Unicode etiketlerini atlama kodu eşdeğerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6848b-137">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="6848b-138">Puni Code adları yalnızca ASCII karakterleri içerir ve her zaman xn--önekiyle başlar.</span><span class="sxs-lookup"><span data-stu-id="6848b-138">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="6848b-139">Bunun nedeni, DNS sunucularının çoğu yalnızca ASCII karakterlerini desteklediği için Internet 'teki mevcut DNS sunucularını desteklemedir (bkz. RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="6848b-139">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="6848b-140">Yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="6848b-140">Configuration files</span></span>

<span data-ttu-id="6848b-141">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6848b-141">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="6848b-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="6848b-142">Example</span></span>

<span data-ttu-id="6848b-143">Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="6848b-143">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6848b-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6848b-144">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="6848b-145">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6848b-145">Network Settings Schema</span></span>](index.md)
