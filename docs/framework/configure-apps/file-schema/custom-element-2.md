---
title: NameValueSectionHandler ve DictionarySectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215490"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="23d14-102">NameValueSectionHandler ve DictionarySectionHandler için özel öğe</span><span class="sxs-lookup"><span data-stu-id="23d14-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="23d14-103">Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="23d14-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a><span data-ttu-id="23d14-104">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="23d14-104">Attributes</span></span>

<span data-ttu-id="23d14-105">Yok</span><span class="sxs-lookup"><span data-stu-id="23d14-105">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="23d14-106">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="23d14-106">Parent element</span></span>

|     | <span data-ttu-id="23d14-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23d14-107">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="23d14-108">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="23d14-108">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="23d14-109">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="23d14-109">Child elements</span></span>

|     | <span data-ttu-id="23d14-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23d14-110">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="23d14-111">[**\<add>**](add-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler>ve için<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="23d14-111">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="23d14-112">Özel uygulama ayarları ekler.</span><span class="sxs-lookup"><span data-stu-id="23d14-112">Adds custom application settings.</span></span> |
| <span data-ttu-id="23d14-113">[**\<remove>**](remove-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler>ve için<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="23d14-113">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="23d14-114">Daha önce tanımlanmış bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="23d14-114">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="23d14-115">[**\<clear>**](clear-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler>ve için<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="23d14-115">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="23d14-116">Bir bölümdeki önceden tanımlanmış tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="23d14-116">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="23d14-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23d14-117">Remarks</span></span>

<span data-ttu-id="23d14-118">**\<sectionName>** Öğesi, öğesinde bir etiketi tarafından tanımlanan özel bir öğedir **\<section>** **\<configSections>** .</span><span class="sxs-lookup"><span data-stu-id="23d14-118">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="23d14-119">Aşağıdaki tabloda, ConfigurationSettings. GetConfig yönteminin her bir yapılandırma bölümü işleyicisi için döndürdüğü nesne türü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="23d14-119">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="23d14-120">Yapılandırma bölümü işleyicisi</span><span class="sxs-lookup"><span data-stu-id="23d14-120">Configuration section handler</span></span>                        | <span data-ttu-id="23d14-121">Dönüş türü</span><span class="sxs-lookup"><span data-stu-id="23d14-121">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="23d14-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="23d14-122">Example</span></span>

<span data-ttu-id="23d14-123">Aşağıdaki örnek, ve sınıflarını kullanan bölümlerin nasıl bildirilemeyeceğini gösterir <xref:System.Configuration.DictionarySectionHandler> <xref:System.Configuration.NameValueSectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="23d14-123">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="23d14-124">İlk özel öğe, **\<dictionarySample>** derleme içindeki sınıf tarafından okunan ayarları içerir <xref:System.Configuration.DictionarySectionHandler> `System.dll` .</span><span class="sxs-lookup"><span data-stu-id="23d14-124">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="23d14-125">İkinci özel öğe, **\<mySection>** derleme içindeki sınıf tarafından okunan ayarları içerir <xref:System.Configuration.NameValueSectionHandler> `System.dll` .</span><span class="sxs-lookup"><span data-stu-id="23d14-125">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="23d14-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="23d14-126">Configuration file</span></span>

<span data-ttu-id="23d14-127">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="23d14-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="23d14-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23d14-128">See also</span></span>

- [<span data-ttu-id="23d14-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="23d14-129">Configuration file schema for the .NET Framework</span></span>](index.md)
