---
title: NameValueSectionHandler ve DictionarySectionHandler özel öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 731e52958b89886c2bc069c4c181c0cc3928d487
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845715"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="6be2b-102">NameValueSectionHandler ve DictionarySectionHandler özel öğesi</span><span class="sxs-lookup"><span data-stu-id="6be2b-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="6be2b-103">Ayarları kullanan özel yapılandırma bölümleri tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="6be2b-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="6be2b-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)\\</span><span class="sxs-lookup"><span data-stu-id="6be2b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)\\</span></span>
<span data-ttu-id="6be2b-105">&nbsp;&nbsp;**\<sectionName >**</span><span class="sxs-lookup"><span data-stu-id="6be2b-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="6be2b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6be2b-106">Attributes</span></span>

<span data-ttu-id="6be2b-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="6be2b-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="6be2b-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="6be2b-108">Parent element</span></span>

|     | <span data-ttu-id="6be2b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be2b-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6be2b-110">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="6be2b-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="6be2b-111">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6be2b-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6be2b-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6be2b-112">Child elements</span></span>

|     | <span data-ttu-id="6be2b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be2b-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="6be2b-114">[**\<Ekle >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) için <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="6be2b-114">[**\<add>**](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="6be2b-115">Özel uygulama ayarları ekler.</span><span class="sxs-lookup"><span data-stu-id="6be2b-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="6be2b-116">[**\<kaldırma >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) için <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="6be2b-116">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="6be2b-117">Önceden tanımlanmış ayar kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6be2b-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="6be2b-118">[**\<Temizle >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) için <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="6be2b-118">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="6be2b-119">Bir bölümdeki tüm önceden tanımlanmış ayarlar temizler.</span><span class="sxs-lookup"><span data-stu-id="6be2b-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6be2b-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6be2b-120">Remarks</span></span>

<span data-ttu-id="6be2b-121"> *\*\<SectionName >** öğedir tarafından tanımlanan özel bir öğe bir  *\*\<bölüm >** içindeki  *\*\<configSections >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="6be2b-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="6be2b-122">Aşağıdaki tabloda, her yapılandırma bölümü işleyicisi için ConfigurationSettings.GetConfig yöntemi nesnenin türü döndürür gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6be2b-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="6be2b-123">Yapılandırma bölümü işleyicisi</span><span class="sxs-lookup"><span data-stu-id="6be2b-123">Configuration section handler</span></span>                        | <span data-ttu-id="6be2b-124">Dönüş türü</span><span class="sxs-lookup"><span data-stu-id="6be2b-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="6be2b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="6be2b-125">Example</span></span>

<span data-ttu-id="6be2b-126">Aşağıdaki örnek, kullanan bölümler bildirmek gösterilmektedir <xref:System.Configuration.DictionarySectionHandler> ve <xref:System.Configuration.NameValueSectionHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="6be2b-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="6be2b-127">İlk özel öğe  **\<dictionarySample >**, UX'te insanlar tarafından ayarları içeren <xref:System.Configuration.DictionarySectionHandler> sınıfını `System.dll` derleme.</span><span class="sxs-lookup"><span data-stu-id="6be2b-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="6be2b-128">İkinci özel öğe  **\<mySection >**, UX'te insanlar tarafından ayarları içeren <xref:System.Configuration.NameValueSectionHandler> sınıfını `System.dll` derleme.</span><span class="sxs-lookup"><span data-stu-id="6be2b-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="6be2b-129">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="6be2b-129">Configuration file</span></span>

<span data-ttu-id="6be2b-130">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="6be2b-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6be2b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6be2b-131">See also</span></span>

- [<span data-ttu-id="6be2b-132">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6be2b-132">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
