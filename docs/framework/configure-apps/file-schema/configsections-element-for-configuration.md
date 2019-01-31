---
title: <configSections> için <configuration> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dc2bb949c7db4f70c20c3c0b687cacafed8696df
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266782"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="793ee-102">\<configSections > öğesi için \<yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="793ee-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="793ee-103">Yapılandırma bölümü ve ad alanı bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="793ee-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="793ee-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="793ee-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="793ee-105">&nbsp;&nbsp;**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="793ee-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="793ee-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="793ee-106">Attributes</span></span>

<span data-ttu-id="793ee-107">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="793ee-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="793ee-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="793ee-108">Parent element</span></span>

|     | <span data-ttu-id="793ee-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="793ee-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="793ee-110">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="793ee-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="793ee-111">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="793ee-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="793ee-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="793ee-112">Child elements</span></span>

|     | <span data-ttu-id="793ee-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="793ee-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="793ee-114">**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="793ee-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="793ee-115">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="793ee-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="793ee-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="793ee-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="793ee-117">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="793ee-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="793ee-118">**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="793ee-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="793ee-119">Önceden tanımlanmış bir bölüm veya bölüm grubu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="793ee-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="793ee-120">**\<Temizleme >**</span><span class="sxs-lookup"><span data-stu-id="793ee-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="793ee-121">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="793ee-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="793ee-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="793ee-122">Remarks</span></span>

<span data-ttu-id="793ee-123">Bu öğe bir yapılandırma dosyasında, ilk alt öğesi olmalıdır  **\<yapılandırma >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="793ee-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="793ee-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="793ee-124">Example</span></span>

<span data-ttu-id="793ee-125">Aşağıdaki örnek, bir yapılandırma bölümü tanımlayın ve bu bölümün ayarlarını tanımlamak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="793ee-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="793ee-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="793ee-126">Configuration file</span></span>

<span data-ttu-id="793ee-127">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="793ee-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="793ee-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="793ee-128">See also</span></span>

- [<span data-ttu-id="793ee-129">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="793ee-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
