---
description: 'İçin: öğesi hakkında daha fazla bilgi <configSections><configuration>'
title: <configuration> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 543ceed8d53fd299e8a0b65594592b64d6b833a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699004"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="71835-103">\<configuration> için \<configSections> öğesi</span><span class="sxs-lookup"><span data-stu-id="71835-103">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="71835-104">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="71835-104">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="71835-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="71835-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="71835-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="71835-106">Attributes</span></span>

<span data-ttu-id="71835-107">Yok</span><span class="sxs-lookup"><span data-stu-id="71835-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="71835-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="71835-108">Parent element</span></span>

|     | <span data-ttu-id="71835-109">Description</span><span class="sxs-lookup"><span data-stu-id="71835-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="71835-110">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="71835-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="71835-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="71835-111">Child elements</span></span>

|     | <span data-ttu-id="71835-112">Description</span><span class="sxs-lookup"><span data-stu-id="71835-112">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="71835-113">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="71835-113">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="71835-114">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="71835-114">Defines a namespace for configuration sections.</span></span> |

## <a name="remarks"></a><span data-ttu-id="71835-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71835-115">Remarks</span></span>

<span data-ttu-id="71835-116">Bu öğe bir yapılandırma dosyasında ise, öğesinin ilk alt öğesi olması gerekir **\<configuration>** .</span><span class="sxs-lookup"><span data-stu-id="71835-116">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="71835-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="71835-117">Example</span></span>

<span data-ttu-id="71835-118">Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="71835-118">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="71835-119">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="71835-119">Configuration file</span></span>

<span data-ttu-id="71835-120">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71835-120">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="71835-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71835-121">See also</span></span>

- [<span data-ttu-id="71835-122">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="71835-122">Configuration file schema for the .NET Framework</span></span>](index.md)
