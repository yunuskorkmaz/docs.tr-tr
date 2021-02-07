---
description: 'Hakkında daha fazla bilgi edinin: NameValueSectionHandler ve DictionarySectionHandler için özel öğe'
title: NameValueSectionHandler ve DictionarySectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: c1bb5b2fb321e2cc9235e02be2158c0875d42032
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698732"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="430ed-103">NameValueSectionHandler ve DictionarySectionHandler için özel öğe</span><span class="sxs-lookup"><span data-stu-id="430ed-103">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="430ed-104">Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="430ed-104">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a><span data-ttu-id="430ed-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="430ed-105">Attributes</span></span>

<span data-ttu-id="430ed-106">Yok</span><span class="sxs-lookup"><span data-stu-id="430ed-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="430ed-107">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="430ed-107">Parent element</span></span>

|     | <span data-ttu-id="430ed-108">Description</span><span class="sxs-lookup"><span data-stu-id="430ed-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="430ed-109">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="430ed-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="430ed-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="430ed-110">Child elements</span></span>

|     | <span data-ttu-id="430ed-111">Description</span><span class="sxs-lookup"><span data-stu-id="430ed-111">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="430ed-112">[**\<add>**](add-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler>ve için<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="430ed-112">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="430ed-113">Özel uygulama ayarları ekler.</span><span class="sxs-lookup"><span data-stu-id="430ed-113">Adds custom application settings.</span></span> |
| <span data-ttu-id="430ed-114">[**\<remove>**](remove-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler>ve için<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="430ed-114">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="430ed-115">Daha önce tanımlanmış bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="430ed-115">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="430ed-116">[**\<clear>**](clear-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler>ve için<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="430ed-116">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="430ed-117">Bir bölümdeki önceden tanımlanmış tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="430ed-117">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="430ed-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="430ed-118">Remarks</span></span>

<span data-ttu-id="430ed-119">**\<sectionName>** Öğesi, öğesinde bir etiketi tarafından tanımlanan özel bir öğedir **\<section>** **\<configSections>** .</span><span class="sxs-lookup"><span data-stu-id="430ed-119">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="430ed-120">Aşağıdaki tabloda, ConfigurationSettings. GetConfig yönteminin her bir yapılandırma bölümü işleyicisi için döndürdüğü nesne türü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="430ed-120">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="430ed-121">Yapılandırma bölümü işleyicisi</span><span class="sxs-lookup"><span data-stu-id="430ed-121">Configuration section handler</span></span>                        | <span data-ttu-id="430ed-122">Dönüş türü</span><span class="sxs-lookup"><span data-stu-id="430ed-122">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="430ed-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="430ed-123">Example</span></span>

<span data-ttu-id="430ed-124">Aşağıdaki örnek, ve sınıflarını kullanan bölümlerin nasıl bildirilemeyeceğini gösterir <xref:System.Configuration.DictionarySectionHandler> <xref:System.Configuration.NameValueSectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="430ed-124">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="430ed-125">İlk özel öğe, **\<dictionarySample>** derleme içindeki sınıf tarafından okunan ayarları içerir <xref:System.Configuration.DictionarySectionHandler> `System.dll` .</span><span class="sxs-lookup"><span data-stu-id="430ed-125">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="430ed-126">İkinci özel öğe, **\<mySection>** derleme içindeki sınıf tarafından okunan ayarları içerir <xref:System.Configuration.NameValueSectionHandler> `System.dll` .</span><span class="sxs-lookup"><span data-stu-id="430ed-126">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="430ed-127">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="430ed-127">Configuration file</span></span>

<span data-ttu-id="430ed-128">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="430ed-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="430ed-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="430ed-129">See also</span></span>

- [<span data-ttu-id="430ed-130">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="430ed-130">Configuration file schema for the .NET Framework</span></span>](index.md)
