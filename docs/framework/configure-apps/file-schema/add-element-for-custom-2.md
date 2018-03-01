---
title: "&lt;ekleme&gt; NameValueSectionHandler ve DictionarySectionHandler öğesi"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e29d0007820bb0218338394fe199e7acfd66344e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="496a9-102">\<Ekle > öğesi NameValueSectionHandler ve DictionarySectionHandler için</span><span class="sxs-lookup"><span data-stu-id="496a9-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="496a9-103">Özel uygulama ayarlarını ekler.</span><span class="sxs-lookup"><span data-stu-id="496a9-103">Adds custom application settings.</span></span> <span data-ttu-id="496a9-104">Her  **\<Ekle >** etiketi bir anahtar/değer çifti içerir.</span><span class="sxs-lookup"><span data-stu-id="496a9-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="496a9-105">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="496a9-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="496a9-106">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="496a9-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="496a9-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="496a9-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="496a9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="496a9-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="496a9-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="496a9-109">Attributes</span></span>

| <span data-ttu-id="496a9-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="496a9-110">Attribute</span></span> | <span data-ttu-id="496a9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="496a9-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="496a9-112">**anahtarı**</span><span class="sxs-lookup"><span data-stu-id="496a9-112">**key**</span></span>   | <span data-ttu-id="496a9-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="496a9-113">Required attribute.</span></span><br><br><span data-ttu-id="496a9-114">Ayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="496a9-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="496a9-115">**value**</span><span class="sxs-lookup"><span data-stu-id="496a9-115">**value**</span></span> | <span data-ttu-id="496a9-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="496a9-116">Required attribute.</span></span><br><br><span data-ttu-id="496a9-117">Ayarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="496a9-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="496a9-118">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="496a9-118">Parent element</span></span>

| <span data-ttu-id="496a9-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="496a9-119">Element</span></span> | <span data-ttu-id="496a9-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="496a9-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="496a9-121">**\<sectionName >** öğesi</span><span class="sxs-lookup"><span data-stu-id="496a9-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="496a9-122">Kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="496a9-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="496a9-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="496a9-123">Child elements</span></span>

<span data-ttu-id="496a9-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="496a9-124">None</span></span>

## <a name="example"></a><span data-ttu-id="496a9-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="496a9-125">Example</span></span>

<span data-ttu-id="496a9-126">Aşağıdaki örnekte bir özel yapılandırma bölümü tanımlama ve kullanma gösterilmektedir  **\<Ekle >** bölüme ayarları yerleştirilecek öğe:</span><span class="sxs-lookup"><span data-stu-id="496a9-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="496a9-127">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="496a9-127">Configuration file</span></span>

<span data-ttu-id="496a9-128">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="496a9-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="496a9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="496a9-129">See also</span></span>

[<span data-ttu-id="496a9-130">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="496a9-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
