---
title: Singletagsectionhandler özel öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bfc2a916e37ac27d45746eb268912b3752f4d80f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705304"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="d45aa-102">Singletagsectionhandler özel öğesi</span><span class="sxs-lookup"><span data-stu-id="d45aa-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="d45aa-103">Ayarları tarafından tanımlanan özel bir yapılandırma bölümünü tanımlayan bir \<bölüm > öğesi ve kullanımları <xref:System.Configuration.SingleTagSectionHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d45aa-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="d45aa-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d45aa-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d45aa-105">&nbsp;&nbsp;*\<sectionName >*</span><span class="sxs-lookup"><span data-stu-id="d45aa-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="d45aa-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d45aa-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="d45aa-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d45aa-107">Attributes</span></span>

<span data-ttu-id="d45aa-108">Kullanıcı tanımlı öznitelikler ve öznitelik değerleri var.</span><span class="sxs-lookup"><span data-stu-id="d45aa-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="d45aa-109">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="d45aa-109">Parent element</span></span>

|     | <span data-ttu-id="d45aa-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d45aa-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d45aa-111">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="d45aa-111">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="d45aa-112">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d45aa-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d45aa-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d45aa-113">Child elements</span></span>

<span data-ttu-id="d45aa-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="d45aa-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d45aa-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d45aa-115">Remarks</span></span>

<span data-ttu-id="d45aa-116"> *\*\<SectionName >** öğedir tarafından tanımlanan özel bir öğe bir [  *\*\<bölüm >** ](~/docs/framework/configure-apps/file-schema/section-element.md) içindeki [  *\*\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d45aa-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="d45aa-117">Yapılandırma sistemi döndürür bir <xref:System.Collections.IDictionary> nesne çağırdığınızda <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d45aa-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="d45aa-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d45aa-118">Example</span></span>

<span data-ttu-id="d45aa-119">Aşağıdaki örnekte adlı özel bir öğe bildirir  **\<sampleSection >** tarafından okunur ayarları içeren <xref:System.Configuration.SingleTagSectionHandler> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="d45aa-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="d45aa-120">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="d45aa-120">Configuration file</span></span>

<span data-ttu-id="d45aa-121">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="d45aa-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d45aa-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d45aa-122">See also</span></span>

- [<span data-ttu-id="d45aa-123">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d45aa-123">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
