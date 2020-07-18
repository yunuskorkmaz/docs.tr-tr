---
title: <configuration> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 1e4bb7a7cfb0b140ca6d13c162708c3c30bd496d
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441693"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="19471-102">\<configuration> için \<configSections> öğesi</span><span class="sxs-lookup"><span data-stu-id="19471-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="19471-103">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="19471-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="19471-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="19471-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="19471-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19471-105">Attributes</span></span>

<span data-ttu-id="19471-106">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="19471-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="19471-107">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="19471-107">Parent element</span></span>

|     | <span data-ttu-id="19471-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19471-108">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="19471-109">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="19471-109">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="19471-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="19471-110">Child elements</span></span>

|     | <span data-ttu-id="19471-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19471-111">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="19471-112">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="19471-112">Contains a configuration section declaration.</span></span> |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | <span data-ttu-id="19471-113">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="19471-113">Defines a namespace for configuration sections.</span></span> |

## <a name="remarks"></a><span data-ttu-id="19471-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19471-114">Remarks</span></span>

<span data-ttu-id="19471-115">Bu öğe bir yapılandırma dosyasında ise, öğesinin ilk alt öğesi olması gerekir **\<configuration>** .</span><span class="sxs-lookup"><span data-stu-id="19471-115">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="19471-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="19471-116">Example</span></span>

<span data-ttu-id="19471-117">Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="19471-117">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="19471-118">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="19471-118">Configuration file</span></span>

<span data-ttu-id="19471-119">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19471-119">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="19471-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19471-120">See also</span></span>

- [<span data-ttu-id="19471-121">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="19471-121">Configuration file schema for the .NET Framework</span></span>](index.md)
