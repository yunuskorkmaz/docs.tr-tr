---
title: '&lt;sectionGroup&gt; öğesi için &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
ms.openlocfilehash: b898c81700e95ec9bc94e04c5a76494b7ac4b0dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="d7d65-102">\<sectionGroup > öğesi için \<configSections ></span><span class="sxs-lookup"><span data-stu-id="d7d65-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="d7d65-103">Yapılandırma bölümleri için bir ad alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d7d65-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="d7d65-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d7d65-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d7d65-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d7d65-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="d7d65-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="d7d65-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d7d65-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7d65-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="d7d65-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d7d65-108">Attribute</span></span>

|           | <span data-ttu-id="d7d65-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7d65-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d7d65-110">**Adı**</span><span class="sxs-lookup"><span data-stu-id="d7d65-110">**name**</span></span>  | <span data-ttu-id="d7d65-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d7d65-111">Required attribute.</span></span><br><br><span data-ttu-id="d7d65-112">Tanımladığınız bölüm grubu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7d65-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d7d65-113">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="d7d65-113">Parent element</span></span>

|     | <span data-ttu-id="d7d65-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7d65-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d7d65-115">**\<configSections >** öğesi</span><span class="sxs-lookup"><span data-stu-id="d7d65-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="d7d65-116">Yapılandırma bölümü ve ad alanı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d7d65-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d7d65-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d7d65-117">Child elements</span></span>

|     | <span data-ttu-id="d7d65-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7d65-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d7d65-119">**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="d7d65-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="d7d65-120">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="d7d65-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d7d65-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7d65-121">Remarks</span></span>

<span data-ttu-id="d7d65-122">Bir bölüm grubu bildirme yapılandırma bölümlerinin için bir kapsayıcı etiket oluşturur ve başka bir kullanıcı tarafından tanımlanan yapılandırma bölümlerinin ile adlandırma çakışmalar olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7d65-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="d7d65-123">Geçirebilmenize  **\<sectionGroup >** birbirine içindeki öğeler.</span><span class="sxs-lookup"><span data-stu-id="d7d65-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="d7d65-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7d65-124">Example</span></span>

<span data-ttu-id="d7d65-125">Aşağıdaki örnek, bir bölüm grubu bildirme ve bölümler bölüm grubu içinde bildirme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d7d65-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="d7d65-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="d7d65-126">Configuration file</span></span>

<span data-ttu-id="d7d65-127">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="d7d65-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7d65-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7d65-128">See also</span></span>

[<span data-ttu-id="d7d65-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d7d65-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
