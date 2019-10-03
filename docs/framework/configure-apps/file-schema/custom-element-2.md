---
title: NameValueSectionHandler ve DictionarySectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 890269857aaa00ce62195ccb2f4cb184b363b61e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921031"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="01629-102">NameValueSectionHandler ve DictionarySectionHandler için özel öğe</span><span class="sxs-lookup"><span data-stu-id="01629-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="01629-103"><xref:System.Configuration.NameValueSectionHandler> Ve<xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01629-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="01629-104">[ **\<Yapılandırma >** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="01629-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="01629-105">&nbsp;&nbsp; **\<sectionName >**</span><span class="sxs-lookup"><span data-stu-id="01629-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="01629-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="01629-106">Attributes</span></span>

<span data-ttu-id="01629-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="01629-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="01629-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="01629-108">Parent element</span></span>

|     | <span data-ttu-id="01629-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01629-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="01629-110"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="01629-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="01629-111">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="01629-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="01629-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="01629-112">Child elements</span></span>

|     | <span data-ttu-id="01629-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01629-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="01629-114">ve için<xref:System.Configuration.NameValueSectionHandler> > ekleyin [ **\<** ](add-element-for-custom-2.md)<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="01629-114">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="01629-115">Özel uygulama ayarları ekler.</span><span class="sxs-lookup"><span data-stu-id="01629-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="01629-116">ve için<xref:System.Configuration.NameValueSectionHandler> > Kaldır [ **\<** ](remove-element-for-custom-2.md)<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="01629-116">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="01629-117">Daha önce tanımlanmış bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="01629-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="01629-118">ve için<xref:System.Configuration.NameValueSectionHandler> > Temizle [ **\<** ](clear-element-for-custom-2.md)<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="01629-118">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="01629-119">Bir bölümdeki önceden tanımlanmış tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="01629-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="01629-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01629-120">Remarks</span></span>

<span data-ttu-id="01629-121">**\<SectionName>** öğedir tarafından tanımlanan özel bir öğe bir **\<bölüm>** içindeki **\<configSections>** öğesi.</span><span class="sxs-lookup"><span data-stu-id="01629-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="01629-122">Aşağıdaki tabloda, ConfigurationSettings. GetConfig yönteminin her bir yapılandırma bölümü işleyicisi için döndürdüğü nesne türü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="01629-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="01629-123">Yapılandırma bölümü işleyicisi</span><span class="sxs-lookup"><span data-stu-id="01629-123">Configuration section handler</span></span>                        | <span data-ttu-id="01629-124">Dönüş türü</span><span class="sxs-lookup"><span data-stu-id="01629-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="01629-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="01629-125">Example</span></span>

<span data-ttu-id="01629-126">Aşağıdaki örnek, <xref:System.Configuration.DictionarySectionHandler> ve <xref:System.Configuration.NameValueSectionHandler> sınıflarını kullanan bölümlerin nasıl bildirilemeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="01629-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="01629-127">İlk özel öğe <xref:System.Configuration.DictionarySectionHandler>  **\<** , `System.dll` derlemedeki sınıf tarafından okunan ayarları içeren dictionarysample >.</span><span class="sxs-lookup"><span data-stu-id="01629-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="01629-128">İkinci özel öğe <xref:System.Configuration.NameValueSectionHandler> `System.dll`  **\<** , derleme içindeki sınıf tarafından okunan ayarları içeren MySection >.</span><span class="sxs-lookup"><span data-stu-id="01629-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="01629-129">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="01629-129">Configuration file</span></span>

<span data-ttu-id="01629-130">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01629-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="01629-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01629-131">See also</span></span>

- [<span data-ttu-id="01629-132">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="01629-132">Configuration file schema for the .NET Framework</span></span>](index.md)
