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
ms.openlocfilehash: d522d004630dee942e24c39a936feae7dc957bd5
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300786"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="3c4cc-102">\<configSections > öğesi için \<yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3c4cc-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="3c4cc-103">Yapılandırma bölümü ve ad alanı bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="3c4cc-104">[ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3c4cc-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="3c4cc-105">&nbsp;&nbsp; **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="3c4cc-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="3c4cc-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3c4cc-106">Attributes</span></span>

<span data-ttu-id="3c4cc-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="3c4cc-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="3c4cc-108">Parent element</span></span>

|     | <span data-ttu-id="3c4cc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c4cc-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3c4cc-110"> *\*\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="3c4cc-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="3c4cc-111">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3c4cc-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3c4cc-112">Child elements</span></span>

|     | <span data-ttu-id="3c4cc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c4cc-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3c4cc-114"> *\*\<Bölüm >** </span><span class="sxs-lookup"><span data-stu-id="3c4cc-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="3c4cc-115">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="3c4cc-116"> *\*\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="3c4cc-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="3c4cc-117">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="3c4cc-118"> *\*\<kaldırma >** </span><span class="sxs-lookup"><span data-stu-id="3c4cc-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="3c4cc-119">Önceden tanımlanmış bir bölüm veya bölüm grubu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="3c4cc-120"> *\*\<Temizleme >** </span><span class="sxs-lookup"><span data-stu-id="3c4cc-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="3c4cc-121">Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3c4cc-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c4cc-122">Remarks</span></span>

<span data-ttu-id="3c4cc-123">Bu öğe bir yapılandırma dosyasında, ilk alt öğesi olmalıdır  **\<yapılandırma >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="3c4cc-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c4cc-124">Example</span></span>

<span data-ttu-id="3c4cc-125">Aşağıdaki örnek, bir yapılandırma bölümü tanımlayın ve bu bölümün ayarlarını tanımlamak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3c4cc-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="3c4cc-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="3c4cc-126">Configuration file</span></span>

<span data-ttu-id="3c4cc-127">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c4cc-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c4cc-128">See also</span></span>

- [<span data-ttu-id="3c4cc-129">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="3c4cc-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
