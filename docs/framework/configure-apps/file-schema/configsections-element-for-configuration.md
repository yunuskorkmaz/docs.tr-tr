---
title: '&lt;configSections&gt; öğesi için &lt;yapılandırma&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 33406a67389cdf857fa5030e20d8a4dec7662741
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="501e6-102">\<configSections > öğesi için \<yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="501e6-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="501e6-103">Yapılandırma bölümü ve ad alanı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="501e6-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="501e6-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="501e6-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="501e6-105">&nbsp;&nbsp;**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="501e6-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="501e6-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="501e6-106">Attributes</span></span>

<span data-ttu-id="501e6-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="501e6-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="501e6-108">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="501e6-108">Parent element</span></span>

|     | <span data-ttu-id="501e6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="501e6-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="501e6-110">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="501e6-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="501e6-111">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="501e6-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="501e6-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="501e6-112">Child elements</span></span>

|     | <span data-ttu-id="501e6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="501e6-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="501e6-114">**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="501e6-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="501e6-115">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="501e6-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="501e6-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="501e6-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="501e6-117">Yapılandırma bölümleri için bir ad alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="501e6-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="501e6-118">**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="501e6-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="501e6-119">Önceden tanımlanmış bölüm veya bölüm grubu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="501e6-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="501e6-120">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="501e6-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="501e6-121">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="501e6-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="501e6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="501e6-122">Remarks</span></span>

<span data-ttu-id="501e6-123">Bu öğe bir yapılandırma dosyası ise, ilk alt öğesi olmalıdır  **\<configuration >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="501e6-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="501e6-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="501e6-124">Example</span></span>

<span data-ttu-id="501e6-125">Aşağıdaki örnek, bir yapılandırma bölümü ve o bölümün ayarlarının tanımlamaya gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="501e6-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="501e6-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="501e6-126">Configuration file</span></span>

<span data-ttu-id="501e6-127">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="501e6-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="501e6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="501e6-128">See also</span></span>

[<span data-ttu-id="501e6-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="501e6-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
