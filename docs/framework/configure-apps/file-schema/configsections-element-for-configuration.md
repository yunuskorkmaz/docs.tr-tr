---
title: <configuration> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927666"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="0f97b-102">\<> yapılandırma için \<configSections > öğesi</span><span class="sxs-lookup"><span data-stu-id="0f97b-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="0f97b-103">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0f97b-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="0f97b-104">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0f97b-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="0f97b-105">&nbsp;&nbsp; **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="0f97b-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="0f97b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0f97b-106">Attributes</span></span>

<span data-ttu-id="0f97b-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="0f97b-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="0f97b-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="0f97b-108">Parent element</span></span>

|     | <span data-ttu-id="0f97b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f97b-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0f97b-110"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="0f97b-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="0f97b-111">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0f97b-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0f97b-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0f97b-112">Child elements</span></span>

|     | <span data-ttu-id="0f97b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f97b-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0f97b-114"> **\<Bölüm >** </span><span class="sxs-lookup"><span data-stu-id="0f97b-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="0f97b-115">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="0f97b-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="0f97b-116"> **\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="0f97b-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="0f97b-117">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f97b-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="0f97b-118"> **\<> Kaldır**</span><span class="sxs-lookup"><span data-stu-id="0f97b-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="0f97b-119">Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0f97b-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="0f97b-120"> **\<> Temizle**</span><span class="sxs-lookup"><span data-stu-id="0f97b-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="0f97b-121">Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.</span><span class="sxs-lookup"><span data-stu-id="0f97b-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="0f97b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f97b-122">Remarks</span></span>

<span data-ttu-id="0f97b-123">Bu öğe bir yapılandırma dosyasında ise,  **\<Yapılandırma >** öğesinin ilk alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f97b-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="0f97b-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f97b-124">Example</span></span>

<span data-ttu-id="0f97b-125">Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="0f97b-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="0f97b-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="0f97b-126">Configuration file</span></span>

<span data-ttu-id="0f97b-127">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f97b-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f97b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f97b-128">See also</span></span>

- [<span data-ttu-id="0f97b-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="0f97b-129">Configuration file schema for the .NET Framework</span></span>](index.md)
