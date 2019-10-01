---
title: <idn> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698168"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="0f87d-102">\<ıdn > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="0f87d-102">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="0f87d-103">Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0f87d-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[<span data-ttu-id="0f87d-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="0f87d-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0f87d-105">&nbsp; @ no__t-1[ **\<urı >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0f87d-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="0f87d-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<ıdn >**</span><span class="sxs-lookup"><span data-stu-id="0f87d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f87d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f87d-107">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f87d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f87d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0f87d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f87d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f87d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0f87d-110">Attributes</span></span>  

|<span data-ttu-id="0f87d-111">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="0f87d-111">**Element**</span></span>|<span data-ttu-id="0f87d-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0f87d-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="0f87d-113">Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir varsayılan değer None ' dır.</span><span class="sxs-lookup"><span data-stu-id="0f87d-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="0f87d-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0f87d-114">Child elements</span></span>

<span data-ttu-id="0f87d-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="0f87d-115">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="0f87d-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="0f87d-116">Parent elements</span></span>

|<span data-ttu-id="0f87d-117">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="0f87d-117">**Element**</span></span>|<span data-ttu-id="0f87d-118">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="0f87d-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0f87d-119">kullanılmamışsa</span><span class="sxs-lookup"><span data-stu-id="0f87d-119">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="0f87d-120">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="0f87d-120">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="0f87d-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f87d-121">Remarks</span></span>

<span data-ttu-id="0f87d-122">Mevcut <xref:System.Uri> sınıfı .NET Framework 3,5 ' de genişletildi.</span><span class="sxs-lookup"><span data-stu-id="0f87d-122">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="0f87d-123">3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) desteğiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0f87d-123">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="0f87d-124">IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="0f87d-124">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="0f87d-125">Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f87d-125">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="0f87d-126">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="0f87d-126">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="0f87d-127">Aşağıdaki satırı .NET Framework 2,0 dizinindeki Machine. config dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0f87d-127">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="0f87d-128">Uluslararası etki alanı adı (ıDN) ayrıştırmayı etki alanı adına uygulanıp uygulanmayacağını ve IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="0f87d-128">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="0f87d-129">Bu, Machine. config veya App. config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f87d-129">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="0f87d-130">Kullanılan DNS sunucularına bağlı olarak ıDN için üç olası değer vardır:</span><span class="sxs-lookup"><span data-stu-id="0f87d-130">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="0f87d-131">IDN etkin = tümü</span><span class="sxs-lookup"><span data-stu-id="0f87d-131">idn enabled = All</span></span>  

     <span data-ttu-id="0f87d-132">Bu değer, herhangi bir Unicode etki alanı adını, zayıf kod eşdeğerlerine (ıDN adları) dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0f87d-132">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="0f87d-133">IDN etkin = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="0f87d-133">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="0f87d-134">Bu değer, yerel Intranette bulunmayan tüm Unicode etki alanı adlarını, Punyıcode eşdeğerlerini (ıDN adları) kullanacak şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0f87d-134">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="0f87d-135">Bu durumda, yerel Intranetteki uluslararası adları işlemek için, Intranet için kullanılan DNS sunucularının Unicode ad çözümlemesini desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f87d-135">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="0f87d-136">IDN etkin = yok</span><span class="sxs-lookup"><span data-stu-id="0f87d-136">idn enabled = None</span></span>

     <span data-ttu-id="0f87d-137">Bu değer, herhangi bir Unicode etki alanı adını Punyıcode kullanacak şekilde dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="0f87d-137">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="0f87d-138">Bu, .NET Framework 2,0 davranışıyla tutarlı olan varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="0f87d-138">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="0f87d-139">IDN 'yi etkinleştirmek, bir etki alanı adındaki tüm Unicode etiketlerini atlama kodu eşdeğerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0f87d-139">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="0f87d-140">Puni Code adları yalnızca ASCII karakterleri içerir ve her zaman xn--önekiyle başlar.</span><span class="sxs-lookup"><span data-stu-id="0f87d-140">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="0f87d-141">Bunun nedeni, DNS sunucularının çoğu yalnızca ASCII karakterlerini desteklediği için Internet 'teki mevcut DNS sunucularını desteklemedir (bkz. RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="0f87d-141">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="0f87d-142">Yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="0f87d-142">Configuration files</span></span>

<span data-ttu-id="0f87d-143">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f87d-143">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="0f87d-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f87d-144">Example</span></span>

<span data-ttu-id="0f87d-145">Aşağıdaki örnek, IRI ayrıştırma ve ıDN adlarını desteklemek için <xref:System.Uri> sınıfı tarafından kullanılan bir yapılandırmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="0f87d-145">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0f87d-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f87d-146">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="0f87d-147">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0f87d-147">Network Settings Schema</span></span>](index.md)
