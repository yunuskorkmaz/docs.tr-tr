---
title: "Özel öğe SingleTagSectionHandler için"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ee722c7d5db9d58ab1a91f4b1299912981510af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="a30a6-102">Özel öğe SingleTagSectionHandler için</span><span class="sxs-lookup"><span data-stu-id="a30a6-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="a30a6-103">Tarafından tanımlanan bir özel yapılandırma bölümünde ayarlarını tanımlayan bir</span><span class="sxs-lookup"><span data-stu-id="a30a6-103">Defines settings in a custom configuration section that is defined by a</span></span> <section> <span data-ttu-id="a30a6-104">öğe ve kullandığı <xref:System.Configuration.SingleTagSectionHandler> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a30a6-104">element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="a30a6-105">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a30a6-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a30a6-106">&nbsp;&nbsp;*\<sectionName >*</span><span class="sxs-lookup"><span data-stu-id="a30a6-106">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="a30a6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a30a6-107">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="a30a6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a30a6-108">Attributes</span></span>

<span data-ttu-id="a30a6-109">Kullanıcı tanımlı, öznitelikler ve öznitelik değerleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="a30a6-109">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="a30a6-110">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="a30a6-110">Parent element</span></span>

|     | <span data-ttu-id="a30a6-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a30a6-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a30a6-112">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="a30a6-112">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="a30a6-113">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a30a6-113">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a30a6-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a30a6-114">Child elements</span></span>

<span data-ttu-id="a30a6-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="a30a6-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="a30a6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a30a6-116">Remarks</span></span>

<span data-ttu-id="a30a6-117"> **\<SectionName >** öğesidir tarafından tanımlanan bir özel bir [  **\<bölüm >** ](~/docs/framework/configure-apps/file-schema/section-element.md) içinde etiketi [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a30a6-117">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="a30a6-118">Yapılandırma sistemi döndüren bir <xref:System.Collections.IDictionary> nesne çağırdığınızda <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a30a6-118">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="a30a6-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a30a6-119">Example</span></span>

<span data-ttu-id="a30a6-120">Aşağıdaki örnek adlı özel bir öğe bildirir  **\<sampleSection >** tarafından okunur ayarları içeren <xref:System.Configuration.SingleTagSectionHandler> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="a30a6-120">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a30a6-121">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="a30a6-121">Configuration file</span></span>

<span data-ttu-id="a30a6-122">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="a30a6-122">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a30a6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a30a6-123">See also</span></span>

[<span data-ttu-id="a30a6-124">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="a30a6-124">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
