---
title: "&lt;IDN&gt; öğesi (URI ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1f631f41c256e74e9b7bf7dc2d771ee156538820
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="c9c26-102">&lt;IDN&gt; öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="c9c26-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="c9c26-103">Bir etki alanı adı Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanmış olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9c26-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="c9c26-104">Şema hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="c9c26-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="c9c26-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="c9c26-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="c9c26-106">\<URI > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="c9c26-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="c9c26-107">\<IDN ></span><span class="sxs-lookup"><span data-stu-id="c9c26-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="c9c26-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9c26-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9c26-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9c26-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c9c26-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9c26-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9c26-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9c26-111">Attributes</span></span>  
  
|<span data-ttu-id="c9c26-112">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="c9c26-112">**Element**</span></span>|<span data-ttu-id="c9c26-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c9c26-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="c9c26-114">Bir etki alanı adı Uluslararası yapılan etki alanı adı (IDN) ayrıştırma uygulanırsa Yok'tur varsayılan değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9c26-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9c26-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9c26-115">Child Elements</span></span>  
 <span data-ttu-id="c9c26-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9c26-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9c26-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9c26-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c9c26-118">**Öğesi**</span><span class="sxs-lookup"><span data-stu-id="c9c26-118">**Element**</span></span>|<span data-ttu-id="c9c26-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="c9c26-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c9c26-120">URI</span><span class="sxs-lookup"><span data-stu-id="c9c26-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="c9c26-121">.NET Framework Tekdüzen Kaynak Tanımlayıcıları (URI'ler) kullanılarak ifade web adresleri işleme biçimini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="c9c26-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9c26-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9c26-122">Remarks</span></span>  
 <span data-ttu-id="c9c26-123">Varolan <xref:System.Uri> sınıf .NET Framework 3. 5 ' genişletilmişse.</span><span class="sxs-lookup"><span data-stu-id="c9c26-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="c9c26-124">3.0 SP1 ve 2.0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve Uluslararası yapılan etki alanı adları (IDN) desteği.</span><span class="sxs-lookup"><span data-stu-id="c9c26-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="c9c26-125">Geçerli kullanıcı özellikle IRI ve IDN etkinleştirmediğiniz sürece herhangi bir değişiklik .NET Framework 2.0 davranış görmezsiniz destekler.</span><span class="sxs-lookup"><span data-stu-id="c9c26-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="c9c26-126">Bu, .NET Framework'ün önceki sürümler ile uygulama uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9c26-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c9c26-127">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="c9c26-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="c9c26-128">.NET Framework 2.0 dizini altındaki machine.config dosyasının aşağıdaki satırı ekleyin</span><span class="sxs-lookup"><span data-stu-id="c9c26-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="c9c26-129">Uluslararası yapılan etki alanı adı (IDN) ayrıştırma için etki alanı adı uygulanan isteyip istemediğinizi ve kuralları ayrıştırma IRI uygulanıp belirtin.</span><span class="sxs-lookup"><span data-stu-id="c9c26-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="c9c26-130">Machine.config veya app.config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9c26-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="c9c26-131">IDN için kullanılan DNS sunucularını bağlı olarak üç olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c9c26-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="c9c26-132">Etkin IDN = All</span><span class="sxs-lookup"><span data-stu-id="c9c26-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="c9c26-133">Bu değer, zayıf kod eşdeğerlerine (IDN adları) Unicode etki alanı adlarını dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c9c26-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="c9c26-134">Etkin IDN AllExceptIntranet =</span><span class="sxs-lookup"><span data-stu-id="c9c26-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="c9c26-135">Bu değer Punycode eşdeğerleri (IDN adları) kullanmak için değil yerel Intranet üzerindeki tüm Unicode etki alanı adlarını dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c9c26-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="c9c26-136">Bu durumda yerel Intranet üzerindeki uluslararası adları işlemek için Intranet için kullanılan DNS sunucularını Unicode ad çözümlemesi desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="c9c26-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="c9c26-137">Etkin IDN = yok</span><span class="sxs-lookup"><span data-stu-id="c9c26-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="c9c26-138">Bu değer, zayıf kod kullanmak için Unicode etki alanı adlarını dönüşmez.</span><span class="sxs-lookup"><span data-stu-id="c9c26-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="c9c26-139">.NET Framework 2.0 davranışa tutarlı olan varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="c9c26-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="c9c26-140">Bir etki alanı adındaki tüm Unicode etiketleri IDN etkinleştirme Punycode eşdeğerlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c9c26-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="c9c26-141">Zayıf kod adları yalnızca ASCII karakterler içeren ve her zaman xn--önekiyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="c9c26-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="c9c26-142">Bunun nedeni çoğu DNS sunucuları, yalnızca ASCII karakterleri (RFC 3940 bakın) destekler beri Internet'te var olan DNS sunucuları desteklemektir.</span><span class="sxs-lookup"><span data-stu-id="c9c26-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="c9c26-143">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="c9c26-143">Configuration Files</span></span>  
 <span data-ttu-id="c9c26-144">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9c26-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9c26-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9c26-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c9c26-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9c26-146">Description</span></span>  
 <span data-ttu-id="c9c26-147">Aşağıdaki örnek tarafından kullanılan bir yapılandırma gösterir <xref:System.Uri> IRI ayrıştırma ve IDN adları desteklemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="c9c26-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c9c26-148">Kod</span><span class="sxs-lookup"><span data-stu-id="c9c26-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9c26-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9c26-149">See Also</span></span>  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="c9c26-150">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c9c26-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
