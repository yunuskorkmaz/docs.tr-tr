---
title: Singletagsectionhandler özel öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ad98617cd4e88d1650f67136536b7dd5994233a4
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301149"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="813fa-102">Singletagsectionhandler özel öğesi</span><span class="sxs-lookup"><span data-stu-id="813fa-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="813fa-103">Ayarları tarafından tanımlanan özel bir yapılandırma bölümünü tanımlayan bir \<bölüm > öğesi ve kullanımları <xref:System.Configuration.SingleTagSectionHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="813fa-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="813fa-104">[ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="813fa-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="813fa-105">&nbsp;&nbsp; *\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="813fa-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="813fa-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="813fa-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="813fa-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="813fa-107">Attributes</span></span>

<span data-ttu-id="813fa-108">Kullanıcı tanımlı öznitelikler ve öznitelik değerleri var.</span><span class="sxs-lookup"><span data-stu-id="813fa-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="813fa-109">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="813fa-109">Parent element</span></span>

|     | <span data-ttu-id="813fa-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="813fa-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="813fa-111"> *\*\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="813fa-111">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="813fa-112">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="813fa-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="813fa-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="813fa-113">Child elements</span></span>

<span data-ttu-id="813fa-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="813fa-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="813fa-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="813fa-115">Remarks</span></span>

<span data-ttu-id="813fa-116">**\<SectionName >** öğedir tarafından tanımlanan özel bir öğe bir [  **\<bölüm >** ](~/docs/framework/configure-apps/file-schema/section-element.md) içindeki [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="813fa-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="813fa-117">Yapılandırma sistemi döndürür bir <xref:System.Collections.IDictionary> nesne çağırdığınızda <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="813fa-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="813fa-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="813fa-118">Example</span></span>

<span data-ttu-id="813fa-119">Aşağıdaki örnekte adlı özel bir öğe bildirir  **\<sampleSection >** tarafından okunur ayarları içeren <xref:System.Configuration.SingleTagSectionHandler> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="813fa-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="813fa-120">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="813fa-120">Configuration file</span></span>

<span data-ttu-id="813fa-121">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="813fa-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="813fa-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="813fa-122">See also</span></span>

- [<span data-ttu-id="813fa-123">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="813fa-123">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
