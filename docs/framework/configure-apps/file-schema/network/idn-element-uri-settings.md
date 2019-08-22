---
title: <idn> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 5fe2eafee702be96bfdca80a06af4a040d9ef0f6
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664128"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="d8300-102">\<IDN > öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="d8300-102">\<idn> Element (Uri Settings)</span></span>
<span data-ttu-id="d8300-103">Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8300-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="d8300-104">Şema hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="d8300-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="d8300-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="d8300-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="d8300-106">\<Uri > öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="d8300-106">\<Uri> Element (Uri Settings)</span></span>](uri-element-uri-settings.md)  
  
 [<span data-ttu-id="d8300-107">\<IDN ></span><span class="sxs-lookup"><span data-stu-id="d8300-107">\<idn></span></span>](idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="d8300-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8300-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8300-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8300-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d8300-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8300-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8300-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8300-111">Attributes</span></span>  
  
|<span data-ttu-id="d8300-112">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="d8300-112">**Element**</span></span>|<span data-ttu-id="d8300-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d8300-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="d8300-114">Uluslararası etki alanı adı (ıDN) ayrıştırmanın bir etki alanı adına uygulandığını belirtir varsayılan değer None ' dır.</span><span class="sxs-lookup"><span data-stu-id="d8300-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8300-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8300-115">Child Elements</span></span>  
 <span data-ttu-id="d8300-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="d8300-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8300-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8300-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d8300-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="d8300-118">**Element**</span></span>|<span data-ttu-id="d8300-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="d8300-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d8300-120">uri</span><span class="sxs-lookup"><span data-stu-id="d8300-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="d8300-121">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d8300-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8300-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8300-122">Remarks</span></span>  
 <span data-ttu-id="d8300-123">Mevcut <xref:System.Uri> sınıf .NET Framework 3,5 ' de genişletildi.</span><span class="sxs-lookup"><span data-stu-id="d8300-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="d8300-124">3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) desteğiyle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d8300-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="d8300-125">IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="d8300-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="d8300-126">Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8300-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d8300-127">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="d8300-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="d8300-128">Aşağıdaki satırı .NET Framework 2,0 dizinindeki Machine. config dosyasına ekleyin</span><span class="sxs-lookup"><span data-stu-id="d8300-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="d8300-129">Uluslararası etki alanı adı (ıDN) ayrıştırmayı etki alanı adına uygulanıp uygulanmayacağını ve IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="d8300-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="d8300-130">Bu, Machine. config veya App. config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8300-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="d8300-131">Kullanılan DNS sunucularına bağlı olarak ıDN için üç olası değer vardır:</span><span class="sxs-lookup"><span data-stu-id="d8300-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
- <span data-ttu-id="d8300-132">IDN etkin = tümü</span><span class="sxs-lookup"><span data-stu-id="d8300-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="d8300-133">Bu değer, herhangi bir Unicode etki alanı adını, zayıf kod eşdeğerlerine (ıDN adları) dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d8300-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
- <span data-ttu-id="d8300-134">IDN etkin = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="d8300-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="d8300-135">Bu değer, yerel Intranette bulunmayan tüm Unicode etki alanı adlarını, Punyıcode eşdeğerlerini (ıDN adları) kullanacak şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d8300-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="d8300-136">Bu durumda, yerel Intranetteki uluslararası adları işlemek için, Intranet için kullanılan DNS sunucularının Unicode ad çözümlemesini desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8300-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
- <span data-ttu-id="d8300-137">IDN etkin = yok</span><span class="sxs-lookup"><span data-stu-id="d8300-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="d8300-138">Bu değer, herhangi bir Unicode etki alanı adını Punyıcode kullanacak şekilde dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="d8300-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="d8300-139">Bu, .NET Framework 2,0 davranışı ile uyumlu olan varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d8300-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="d8300-140">IDN 'yi etkinleştirmek, bir etki alanı adındaki tüm Unicode etiketlerini atlama kodu eşdeğerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d8300-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="d8300-141">Puni Code adları yalnızca ASCII karakterleri içerir ve her zaman xn--önekiyle başlar.</span><span class="sxs-lookup"><span data-stu-id="d8300-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="d8300-142">Bunun nedeni, DNS sunucularının çoğu yalnızca ASCII karakterlerini desteklediği için Internet 'teki mevcut DNS sunucularını desteklemedir (bkz. RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="d8300-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="d8300-143">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="d8300-143">Configuration Files</span></span>  
 <span data-ttu-id="d8300-144">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8300-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8300-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8300-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d8300-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8300-146">Description</span></span>  
 <span data-ttu-id="d8300-147">Aşağıdaki örnek, IRI ayrıştırma ve IDN adlarını desteklemek <xref:System.Uri> için sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8300-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d8300-148">Kod</span><span class="sxs-lookup"><span data-stu-id="d8300-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8300-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8300-149">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="d8300-150">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d8300-150">Network Settings Schema</span></span>](index.md)
