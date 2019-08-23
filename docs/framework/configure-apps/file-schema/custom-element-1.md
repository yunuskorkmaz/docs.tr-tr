---
title: SingleTagSectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927497"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="e73cb-102">SingleTagSectionHandler için özel öğe</span><span class="sxs-lookup"><span data-stu-id="e73cb-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="e73cb-103">Bir \<Bölüm > öğesi tarafından tanımlanan ve <xref:System.Configuration.SingleTagSectionHandler> sınıfını kullanan özel bir yapılandırma bölümünde ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e73cb-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="e73cb-104">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e73cb-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="e73cb-105">&nbsp;&nbsp; *\<sectionName >*</span><span class="sxs-lookup"><span data-stu-id="e73cb-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="e73cb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e73cb-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="e73cb-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e73cb-107">Attributes</span></span>

<span data-ttu-id="e73cb-108">Öznitelikler ve öznitelik değerleri Kullanıcı tanımlı ' dır.</span><span class="sxs-lookup"><span data-stu-id="e73cb-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="e73cb-109">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="e73cb-109">Parent element</span></span>

|     | <span data-ttu-id="e73cb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e73cb-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e73cb-111"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="e73cb-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="e73cb-112">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e73cb-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e73cb-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e73cb-113">Child elements</span></span>

<span data-ttu-id="e73cb-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e73cb-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="e73cb-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e73cb-115">Remarks</span></span>

<span data-ttu-id="e73cb-116">SectionName > öğesi, [**configSections \<>** ](configsections-element-for-configuration.md) öğesinde bir [ **\<Bölüm >** ](section-element.md) etiketi tarafından tanımlanan özel bir öğedir.  **\<**</span><span class="sxs-lookup"><span data-stu-id="e73cb-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="e73cb-117">Yapılandırma sistemi, çağırdığınızda <xref:System.Collections.IDictionary> <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="e73cb-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="e73cb-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e73cb-118">Example</span></span>

<span data-ttu-id="e73cb-119">Aşağıdaki örnek, <xref:System.Configuration.SingleTagSectionHandler> sınıf tarafından okunan ayarları içeren  **\<sampleSection >** adlı özel bir öğe bildirir:</span><span class="sxs-lookup"><span data-stu-id="e73cb-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="e73cb-120">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="e73cb-120">Configuration file</span></span>

<span data-ttu-id="e73cb-121">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e73cb-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e73cb-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e73cb-122">See also</span></span>

- [<span data-ttu-id="e73cb-123">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e73cb-123">Configuration file schema for the .NET Framework</span></span>](index.md)
