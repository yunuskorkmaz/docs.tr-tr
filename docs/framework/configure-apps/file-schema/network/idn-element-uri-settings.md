---
title: '&lt;IDN&gt; öğesi (Uri ayarları)'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 96d70f76f8d29368505dd5054edf3db253b89016
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50037015"
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="6180d-102">&lt;IDN&gt; öğesi (Uri ayarları)</span><span class="sxs-lookup"><span data-stu-id="6180d-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="6180d-103">Bir etki alanı adı için Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6180d-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="6180d-104">Şema hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="6180d-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="6180d-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="6180d-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="6180d-106">\<URI > öğesi (Uri ayarları)</span><span class="sxs-lookup"><span data-stu-id="6180d-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="6180d-107">\<IDN ></span><span class="sxs-lookup"><span data-stu-id="6180d-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="6180d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6180d-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6180d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6180d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6180d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6180d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6180d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6180d-111">Attributes</span></span>  
  
|<span data-ttu-id="6180d-112">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6180d-112">**Element**</span></span>|<span data-ttu-id="6180d-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6180d-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="6180d-114">Bir etki alanı adı için Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanırsa Yok'tur varsayılan değeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6180d-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6180d-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6180d-115">Child Elements</span></span>  
 <span data-ttu-id="6180d-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="6180d-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6180d-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6180d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6180d-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="6180d-118">**Element**</span></span>|<span data-ttu-id="6180d-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6180d-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6180d-120">URI</span><span class="sxs-lookup"><span data-stu-id="6180d-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="6180d-121">.NET Framework web adresleri Tekdüzen Kaynak Tanımlayıcıları (URI'lar) kullanılarak ifade nasıl işlediğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="6180d-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6180d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6180d-122">Remarks</span></span>  
 <span data-ttu-id="6180d-123">Varolan <xref:System.Uri> sınıfı, .NET Framework 3.5 genişletilmişse.</span><span class="sxs-lookup"><span data-stu-id="6180d-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="6180d-124">3.0 SP1 ve 2.0 SP1 uluslararası kaynak tanımlayıcı (IRI) ve Uluslararası yapılan etki alanı adı (IDN) desteği.</span><span class="sxs-lookup"><span data-stu-id="6180d-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="6180d-125">Özellikle IRI ve IDN etkinleştirmediğiniz sürece geçerli kullanıcıların .NET Framework 2.0 davranış herhangi bir değişikliği göremezsiniz destekler.</span><span class="sxs-lookup"><span data-stu-id="6180d-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="6180d-126">Bu, .NET Framework'ün önceki sürümleriyle uygulama uyumluluğu sağlar.</span><span class="sxs-lookup"><span data-stu-id="6180d-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="6180d-127">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gerekmez:</span><span class="sxs-lookup"><span data-stu-id="6180d-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="6180d-128">Machine.config dosyasının .NET Framework 2.0 dizininde aşağıdaki satırı ekleyin</span><span class="sxs-lookup"><span data-stu-id="6180d-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="6180d-129">IRI ayrıştırma kurallarını uygulanıp ve etki alanı adına uygulanan Uluslararası yapılan etki alanı adı (IDN) ayrıştırma isteyip istemediğinizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="6180d-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="6180d-130">Bu, machine.config veya app.config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="6180d-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="6180d-131">IDN için kullanılan DNS sunucularını bağlı olarak üç olası değer vardır:</span><span class="sxs-lookup"><span data-stu-id="6180d-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="6180d-132">Etkin IDN = All</span><span class="sxs-lookup"><span data-stu-id="6180d-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="6180d-133">Bu değer herhangi bir Unicode etki alanı adı Punycode eşdeğerleri (IDN adları) dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6180d-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="6180d-134">Etkin IDN AllExceptIntranet =</span><span class="sxs-lookup"><span data-stu-id="6180d-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="6180d-135">Bu değer, tüm Unicode olmayan Yerel Intranet Punycode eşdeğerleri (IDN adı) kullanmak için etki alanı adlarına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6180d-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="6180d-136">Bu durumda yerel Intranet üzerindeki uluslararası adları işlemek için Intranet için kullanılan DNS sunucularını Unicode ad çözümlemesi desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="6180d-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="6180d-137">Etkin IDN = yok</span><span class="sxs-lookup"><span data-stu-id="6180d-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="6180d-138">Bu değer, zayıf kod kullanmak için herhangi bir Unicode etki alanı adı dönüşmez.</span><span class="sxs-lookup"><span data-stu-id="6180d-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="6180d-139">.NET Framework 2.0 davranışı ile tutarlı olan varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="6180d-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="6180d-140">Bir etki alanı adındaki tüm Unicode etiketleri IDN etkinleştirme Punycode eşdeğerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="6180d-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="6180d-141">Zayıf kod adları yalnızca ASCII karakterler içeren ve her zaman xn--önekiyle başlayan.</span><span class="sxs-lookup"><span data-stu-id="6180d-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="6180d-142">Bunun nedeni çoğu DNS sunucuları yalnızca ASCII karakterleri (bkz. RFC 3940) desteklemediğinden Internet'te mevcut DNS sunucuları desteklemektir.</span><span class="sxs-lookup"><span data-stu-id="6180d-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="6180d-143">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6180d-143">Configuration Files</span></span>  
 <span data-ttu-id="6180d-144">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6180d-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6180d-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="6180d-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6180d-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6180d-146">Description</span></span>  
 <span data-ttu-id="6180d-147">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> IRI ayrıştırma ve IDN adları desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="6180d-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6180d-148">Kod</span><span class="sxs-lookup"><span data-stu-id="6180d-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6180d-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6180d-149">See Also</span></span>  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="6180d-150">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6180d-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
