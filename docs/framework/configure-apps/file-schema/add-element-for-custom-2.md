---
title: '&lt;ekleme&gt; NameValueSectionHandler ve DictionarySectionHandler öğesi'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
ms.openlocfilehash: aeb3e3a4be201369ca2df8d231498dd2400d3c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361377"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="66925-102">\<Ekle > öğesi NameValueSectionHandler ve DictionarySectionHandler için</span><span class="sxs-lookup"><span data-stu-id="66925-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="66925-103">Özel uygulama ayarlarını ekler.</span><span class="sxs-lookup"><span data-stu-id="66925-103">Adds custom application settings.</span></span> <span data-ttu-id="66925-104">Her  **\<Ekle >** etiketi bir anahtar/değer çifti içerir.</span><span class="sxs-lookup"><span data-stu-id="66925-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="66925-105">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="66925-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="66925-106">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="66925-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="66925-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="66925-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="66925-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66925-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="66925-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="66925-109">Attributes</span></span>

| <span data-ttu-id="66925-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="66925-110">Attribute</span></span> | <span data-ttu-id="66925-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66925-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="66925-112">**Anahtarı**</span><span class="sxs-lookup"><span data-stu-id="66925-112">**key**</span></span>   | <span data-ttu-id="66925-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="66925-113">Required attribute.</span></span><br><br><span data-ttu-id="66925-114">Ayar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="66925-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="66925-115">**value**</span><span class="sxs-lookup"><span data-stu-id="66925-115">**value**</span></span> | <span data-ttu-id="66925-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="66925-116">Required attribute.</span></span><br><br><span data-ttu-id="66925-117">Ayarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="66925-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="66925-118">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="66925-118">Parent element</span></span>

| <span data-ttu-id="66925-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="66925-119">Element</span></span> | <span data-ttu-id="66925-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66925-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="66925-121">**\<sectionName >** öğesi</span><span class="sxs-lookup"><span data-stu-id="66925-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="66925-122">Kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="66925-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="66925-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="66925-123">Child elements</span></span>

<span data-ttu-id="66925-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="66925-124">None</span></span>

## <a name="example"></a><span data-ttu-id="66925-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="66925-125">Example</span></span>

<span data-ttu-id="66925-126">Aşağıdaki örnekte bir özel yapılandırma bölümü tanımlama ve kullanma gösterilmektedir  **\<Ekle >** bölüme ayarları yerleştirilecek öğe:</span><span class="sxs-lookup"><span data-stu-id="66925-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="66925-127">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="66925-127">Configuration file</span></span>

<span data-ttu-id="66925-128">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="66925-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="66925-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66925-129">See also</span></span>

[<span data-ttu-id="66925-130">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="66925-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
