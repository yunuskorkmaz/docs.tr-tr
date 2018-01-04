---
title: "Özel öğe NameValueSectionHandler ve DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2154e2a178050e5bafa7d19f37a766141d0a5838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="8bcc0-102">Özel öğe NameValueSectionHandler ve DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="8bcc0-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="8bcc0-103">Kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="8bcc0-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8bcc0-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="8bcc0-105">&nbsp;&nbsp;**\<sectionName >**</span><span class="sxs-lookup"><span data-stu-id="8bcc0-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="8bcc0-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8bcc0-106">Attributes</span></span>

<span data-ttu-id="8bcc0-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="8bcc0-108">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="8bcc0-108">Parent element</span></span>

|     | <span data-ttu-id="8bcc0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bcc0-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8bcc0-110">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="8bcc0-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="8bcc0-111">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="8bcc0-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="8bcc0-112">Child elements</span></span>

|     | <span data-ttu-id="8bcc0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bcc0-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="8bcc0-114">[**\<Ekle >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) için <xref:System.Configuration.NameValueSectionHandler> ve<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="8bcc0-114">[**\<add>**](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="8bcc0-115">Özel uygulama ayarlarını ekler.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="8bcc0-116">[**\<kaldırma >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) için <xref:System.Configuration.NameValueSectionHandler> ve<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="8bcc0-116">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> |    <span data-ttu-id="8bcc0-117">Önceden tanımlanmış bir ayar kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="8bcc0-118">[**\<Clear >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) için <xref:System.Configuration.NameValueSectionHandler> ve<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="8bcc0-118">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="8bcc0-119">Bir bölümdeki tüm önceden tanımlanmış ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8bcc0-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bcc0-120">Remarks</span></span>

<span data-ttu-id="8bcc0-121"> **\<SectionName >** öğesidir tarafından tanımlanan bir özel bir  **\<bölüm >** içinde etiketi  **\<configSections >**öğesi.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="8bcc0-122">Aşağıdaki tabloda, her yapılandırma bölümü işleyicisi için nesne ConfigurationSettings.GetConfig yöntemi türünü döndürür gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8bcc0-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="8bcc0-123">Yapılandırma bölümü işleyicisi</span><span class="sxs-lookup"><span data-stu-id="8bcc0-123">Configuration section handler</span></span>                        | <span data-ttu-id="8bcc0-124">Dönüş türü</span><span class="sxs-lookup"><span data-stu-id="8bcc0-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="8bcc0-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bcc0-125">Example</span></span>

<span data-ttu-id="8bcc0-126">Aşağıdaki örnek kullanan bölümler bildirmek nasıl gösterir <xref:System.Configuration.DictionarySectionHandler> ve <xref:System.Configuration.NameValueSectionHandler> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span> 

<span data-ttu-id="8bcc0-127">İlk özel öğe  **\<dictionarySample >**, tarafından okunur ayarları içeren <xref:System.Configuration.DictionarySectionHandler> sınıfını `System.dll` derleme.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="8bcc0-128">İkinci özel öğesi  **\<mySection >**, tarafından okunur ayarları içeren <xref:System.Configuration.NameValueSectionHandler> sınıfını `System.dll` derleme.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="8bcc0-129">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="8bcc0-129">Configuration file</span></span>

<span data-ttu-id="8bcc0-130">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8bcc0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bcc0-131">See also</span></span>

[<span data-ttu-id="8bcc0-132">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="8bcc0-132">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
