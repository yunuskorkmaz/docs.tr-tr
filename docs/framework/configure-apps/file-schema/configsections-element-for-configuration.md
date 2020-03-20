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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155355"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="5fef7-102">\<yapılandırma> için \<configSections> elemanı</span><span class="sxs-lookup"><span data-stu-id="5fef7-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="5fef7-103">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5fef7-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="5fef7-104">yapılandırma &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) **configSections \<>**</span><span class="sxs-lookup"><span data-stu-id="5fef7-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="5fef7-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5fef7-105">Attributes</span></span>

<span data-ttu-id="5fef7-106">None</span><span class="sxs-lookup"><span data-stu-id="5fef7-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="5fef7-107">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="5fef7-107">Parent element</span></span>

|     | <span data-ttu-id="5fef7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fef7-108">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5fef7-109">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="5fef7-109">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="5fef7-110">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5fef7-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5fef7-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="5fef7-111">Child elements</span></span>

|     | <span data-ttu-id="5fef7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fef7-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5fef7-113">**\<bölüm>**</span><span class="sxs-lookup"><span data-stu-id="5fef7-113">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="5fef7-114">Yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="5fef7-114">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="5fef7-115">**\<bölümGrup>**</span><span class="sxs-lookup"><span data-stu-id="5fef7-115">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="5fef7-116">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5fef7-116">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="5fef7-117">**\<>kaldırmak**</span><span class="sxs-lookup"><span data-stu-id="5fef7-117">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="5fef7-118">Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5fef7-118">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="5fef7-119">**\<açık>**</span><span class="sxs-lookup"><span data-stu-id="5fef7-119">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="5fef7-120">Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.</span><span class="sxs-lookup"><span data-stu-id="5fef7-120">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="5fef7-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fef7-121">Remarks</span></span>

<span data-ttu-id="5fef7-122">Bu öğe bir yapılandırma dosyasındaysa, \*\* \<yapılandırma>\*\* öğesinin ilk alt öğesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fef7-122">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="5fef7-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fef7-123">Example</span></span>

<span data-ttu-id="5fef7-124">Aşağıdaki örnekte, yapılandırma bölümünün nasıl tanımlanılıgı ve bu bölümün ayarlarını nasıl tanımlanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5fef7-124">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="5fef7-125">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="5fef7-125">Configuration file</span></span>

<span data-ttu-id="5fef7-126">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fef7-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fef7-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fef7-127">See also</span></span>

- [<span data-ttu-id="5fef7-128">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="5fef7-128">Configuration file schema for the .NET Framework</span></span>](index.md)
