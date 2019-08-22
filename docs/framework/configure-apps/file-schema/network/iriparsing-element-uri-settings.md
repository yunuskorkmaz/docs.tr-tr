---
title: <iriParsing> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 2c99edf2f1a03e0e510858c106cad43b0eaa27b4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664083"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="10625-102">\<ıriayrıştırma > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="10625-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="10625-103">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma 'nin bir <xref:System.Uri> öğesine uygulanıp uygulanmadığını ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="10625-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="10625-104">Şema hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="10625-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="10625-105">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="10625-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="10625-106">\<Uri > öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="10625-106">\<Uri> Element (Uri Settings)</span></span>](uri-element-uri-settings.md)  
  
 [<span data-ttu-id="10625-107">\<ıriayrıştırma ></span><span class="sxs-lookup"><span data-stu-id="10625-107">\<iriParsing></span></span>](iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="10625-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10625-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10625-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10625-109">Attributes and Elements</span></span>  
 <span data-ttu-id="10625-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10625-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10625-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10625-111">Attributes</span></span>  
  
|<span data-ttu-id="10625-112">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="10625-112">**Element**</span></span>|<span data-ttu-id="10625-113">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="10625-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="10625-114">IRI ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10625-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="10625-115">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="10625-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10625-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10625-116">Child Elements</span></span>  
 <span data-ttu-id="10625-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="10625-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10625-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10625-118">Parent Elements</span></span>  
  
|<span data-ttu-id="10625-119">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="10625-119">**Element**</span></span>|<span data-ttu-id="10625-120">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="10625-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="10625-121">uri</span><span class="sxs-lookup"><span data-stu-id="10625-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="10625-122">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="10625-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10625-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10625-123">Remarks</span></span>  
 <span data-ttu-id="10625-124">Mevcut <xref:System.Uri> sınıf .NET Framework 3,5 ' de genişletildi.</span><span class="sxs-lookup"><span data-stu-id="10625-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="10625-125">3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="10625-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="10625-126">IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="10625-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="10625-127">Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="10625-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="10625-128">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="10625-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="10625-129">Aşağıdaki satırı .NET Framework 2,0 dizinindeki Machine. config dosyasına ekleyin</span><span class="sxs-lookup"><span data-stu-id="10625-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="10625-130">IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="10625-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="10625-131">Bu, Machine. config veya App. config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="10625-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="10625-132">IRI ayrıştırma (ıriayrıştırmayı etkin = `true`) etkinleştirildiğinde, RFC 3987 ' deki en son IRI kurallarına göre normalleştirme ve karakter denetimi yapılır.</span><span class="sxs-lookup"><span data-stu-id="10625-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="10625-133">Varsayılan değer, `false` RFC 2396 ve RFC 3986 (IPv6 sabit değerleri için) öğesine göre normalleştirme ve karakter denetimi yapar.</span><span class="sxs-lookup"><span data-stu-id="10625-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="10625-134">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="10625-134">Configuration Files</span></span>  
 <span data-ttu-id="10625-135">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10625-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10625-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="10625-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="10625-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10625-137">Description</span></span>  
 <span data-ttu-id="10625-138">Aşağıdaki örnek, IRI ayrıştırma ve IDN adlarını desteklemek <xref:System.Uri> için sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="10625-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="10625-139">Kod</span><span class="sxs-lookup"><span data-stu-id="10625-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="10625-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10625-140">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="10625-141">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="10625-141">Network Settings Schema</span></span>](index.md)
