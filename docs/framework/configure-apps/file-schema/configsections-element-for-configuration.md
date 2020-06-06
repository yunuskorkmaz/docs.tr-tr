---
title: <configuration> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155355"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="f4e3b-102">\<configuration> için \<configSections> öğesi</span><span class="sxs-lookup"><span data-stu-id="f4e3b-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="f4e3b-103">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="f4e3b-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="f4e3b-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="f4e3b-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4e3b-105">Attributes</span></span>

<span data-ttu-id="f4e3b-106">Yok</span><span class="sxs-lookup"><span data-stu-id="f4e3b-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="f4e3b-107">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="f4e3b-107">Parent element</span></span>

|     | <span data-ttu-id="f4e3b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4e3b-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="f4e3b-109">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f4e3b-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f4e3b-110">Child elements</span></span>

|     | <span data-ttu-id="f4e3b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4e3b-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="f4e3b-112">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="f4e3b-113">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-113">Defines a namespace for configuration sections.</span></span> |
| [**\<remove>**](remove-element-for-configsections.md) | <span data-ttu-id="f4e3b-114">Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-114">Removes a predefined section or section group.</span></span> |
| [**\<clear>**](clear-element-for-configsections.md) | <span data-ttu-id="f4e3b-115">Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-115">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f4e3b-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4e3b-116">Remarks</span></span>

<span data-ttu-id="f4e3b-117">Bu öğe bir yapılandırma dosyasında ise, öğesinin ilk alt öğesi olması gerekir **\<configuration>** .</span><span class="sxs-lookup"><span data-stu-id="f4e3b-117">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="f4e3b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4e3b-118">Example</span></span>

<span data-ttu-id="f4e3b-119">Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f4e3b-119">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="f4e3b-120">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="f4e3b-120">Configuration file</span></span>

<span data-ttu-id="f4e3b-121">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4e3b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4e3b-122">See also</span></span>

- [<span data-ttu-id="f4e3b-123">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="f4e3b-123">Configuration file schema for the .NET Framework</span></span>](index.md)
