---
description: 'Daha fazla bilgi edinin: <iriParsing> öğesi (URI ayarları)'
title: <iriParsing> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 460216b64056cd9c9f769c5bcd1b651d249e98b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740307"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="23b8c-103">\<iriParsing> Öğesi (Uri Ayarları)</span><span class="sxs-lookup"><span data-stu-id="23b8c-103">\<iriParsing> Element (Uri Settings)</span></span>

<span data-ttu-id="23b8c-104">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırma 'nin bir öğesine uygulanıp uygulanmadığını <xref:System.Uri> ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="23b8c-104">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a><span data-ttu-id="23b8c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="23b8c-105">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23b8c-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="23b8c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="23b8c-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="23b8c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23b8c-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="23b8c-108">Attributes</span></span>  
  
|<span data-ttu-id="23b8c-109">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="23b8c-109">**Element**</span></span>|<span data-ttu-id="23b8c-110">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="23b8c-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="23b8c-111">IRI ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="23b8c-111">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="23b8c-112">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="23b8c-112">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23b8c-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="23b8c-113">Child Elements</span></span>  

 <span data-ttu-id="23b8c-114">Yok</span><span class="sxs-lookup"><span data-stu-id="23b8c-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23b8c-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="23b8c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="23b8c-116">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="23b8c-116">**Element**</span></span>|<span data-ttu-id="23b8c-117">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="23b8c-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="23b8c-118">kullanılmamışsa</span><span class="sxs-lookup"><span data-stu-id="23b8c-118">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="23b8c-119">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="23b8c-119">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23b8c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23b8c-120">Remarks</span></span>  

 <span data-ttu-id="23b8c-121">Mevcut <xref:System.Uri> sınıf .NET Framework 3,5 ' de genişletildi.</span><span class="sxs-lookup"><span data-stu-id="23b8c-121">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="23b8c-122">3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="23b8c-122">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="23b8c-123">IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="23b8c-123">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="23b8c-124">Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="23b8c-124">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="23b8c-125">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="23b8c-125">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="23b8c-126">Aşağıdaki satırı .NET Framework 2,0 dizinindeki machine.config dosyasına ekleyin</span><span class="sxs-lookup"><span data-stu-id="23b8c-126">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="23b8c-127">IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="23b8c-127">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="23b8c-128">Bu, machine.config veya app.config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="23b8c-128">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="23b8c-129">IRI ayrıştırma (ıriayrıştırmayı etkin = `true` ) etkinleştirildiğinde, RFC 3987 ' deki en son IRI kurallarına göre normalleştirme ve karakter denetimi yapılır.</span><span class="sxs-lookup"><span data-stu-id="23b8c-129">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="23b8c-130">Varsayılan değer, `false` rfc 2396 ve rfc 3986 (IPv6 sabit değerleri için) öğesine göre normalleştirme ve karakter denetimi yapar.</span><span class="sxs-lookup"><span data-stu-id="23b8c-130">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="23b8c-131">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="23b8c-131">Configuration Files</span></span>  

 <span data-ttu-id="23b8c-132">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="23b8c-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23b8c-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="23b8c-133">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="23b8c-134">Description</span><span class="sxs-lookup"><span data-stu-id="23b8c-134">Description</span></span>  

 <span data-ttu-id="23b8c-135">Aşağıdaki örnek, <xref:System.Uri> IRI ayrıştırma ve IDN adlarını desteklemek için sınıfı tarafından kullanılan bir yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="23b8c-135">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="23b8c-136">Kod</span><span class="sxs-lookup"><span data-stu-id="23b8c-136">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23b8c-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23b8c-137">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="23b8c-138">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="23b8c-138">Network Settings Schema</span></span>](index.md)
