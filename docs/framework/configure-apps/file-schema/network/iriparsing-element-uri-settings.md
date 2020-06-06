---
title: <iriParsing> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698099"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="f54bb-102">\<iriParsing> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="f54bb-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="f54bb-103">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma 'nin bir öğesine uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f54bb-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a><span data-ttu-id="f54bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f54bb-104">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f54bb-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f54bb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f54bb-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f54bb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f54bb-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f54bb-107">Attributes</span></span>  
  
|<span data-ttu-id="f54bb-108">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="f54bb-108">**Element**</span></span>|<span data-ttu-id="f54bb-109">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f54bb-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="f54bb-110">IRI ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f54bb-110">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="f54bb-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="f54bb-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f54bb-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f54bb-112">Child Elements</span></span>  
 <span data-ttu-id="f54bb-113">Yok</span><span class="sxs-lookup"><span data-stu-id="f54bb-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f54bb-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f54bb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f54bb-115">**Dosyalarında**</span><span class="sxs-lookup"><span data-stu-id="f54bb-115">**Element**</span></span>|<span data-ttu-id="f54bb-116">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="f54bb-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f54bb-117">kullanılmamışsa</span><span class="sxs-lookup"><span data-stu-id="f54bb-117">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="f54bb-118">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="f54bb-118">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f54bb-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f54bb-119">Remarks</span></span>  
 <span data-ttu-id="f54bb-120">Mevcut <xref:System.Uri> sınıf .NET Framework 3,5 ' de genişletildi.</span><span class="sxs-lookup"><span data-stu-id="f54bb-120">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="f54bb-121">3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f54bb-121">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="f54bb-122">IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="f54bb-122">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="f54bb-123">Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="f54bb-123">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f54bb-124">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="f54bb-124">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="f54bb-125">Aşağıdaki satırı .NET Framework 2,0 dizinindeki Machine. config dosyasına ekleyin</span><span class="sxs-lookup"><span data-stu-id="f54bb-125">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="f54bb-126">IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f54bb-126">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="f54bb-127">Bu, Machine. config veya App. config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f54bb-127">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="f54bb-128">IRI ayrıştırma (ıriayrıştırmayı etkin = `true` ) etkinleştirildiğinde, RFC 3987 ' deki en son IRI kurallarına göre normalleştirme ve karakter denetimi yapılır.</span><span class="sxs-lookup"><span data-stu-id="f54bb-128">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="f54bb-129">Varsayılan değer, `false` rfc 2396 ve rfc 3986 (IPv6 sabit değerleri için) öğesine göre normalleştirme ve karakter denetimi yapar.</span><span class="sxs-lookup"><span data-stu-id="f54bb-129">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="f54bb-130">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="f54bb-130">Configuration Files</span></span>  
 <span data-ttu-id="f54bb-131">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f54bb-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f54bb-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="f54bb-132">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f54bb-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f54bb-133">Description</span></span>  
 <span data-ttu-id="f54bb-134">Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f54bb-134">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f54bb-135">Kod</span><span class="sxs-lookup"><span data-stu-id="f54bb-135">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f54bb-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f54bb-136">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="f54bb-137">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f54bb-137">Network Settings Schema</span></span>](index.md)
