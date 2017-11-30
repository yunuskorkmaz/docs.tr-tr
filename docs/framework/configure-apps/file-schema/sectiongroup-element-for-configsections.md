---
title: "&lt;sectionGroup&gt; öğesi için &lt;configSections&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c5c040a322c38da319f2e964519f94d761327e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="0dea1-102">\<sectionGroup > öğesi için \<configSections ></span><span class="sxs-lookup"><span data-stu-id="0dea1-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="0dea1-103">Yapılandırma bölümleri için bir ad alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0dea1-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="0dea1-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0dea1-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="0dea1-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="0dea1-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="0dea1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="0dea1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0dea1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dea1-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="0dea1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0dea1-108">Attribute</span></span>

|           | <span data-ttu-id="0dea1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dea1-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="0dea1-110">**adı**</span><span class="sxs-lookup"><span data-stu-id="0dea1-110">**name**</span></span>  | <span data-ttu-id="0dea1-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0dea1-111">Required attribute.</span></span><br><br><span data-ttu-id="0dea1-112">Tanımladığınız bölüm grubu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0dea1-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="0dea1-113">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="0dea1-113">Parent element</span></span>

|     | <span data-ttu-id="0dea1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dea1-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0dea1-115">**\<configSections >** öğesi</span><span class="sxs-lookup"><span data-stu-id="0dea1-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="0dea1-116">Yapılandırma bölümü ve ad alanı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0dea1-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0dea1-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0dea1-117">Child elements</span></span>

|     | <span data-ttu-id="0dea1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dea1-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0dea1-119">**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="0dea1-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="0dea1-120">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="0dea1-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="0dea1-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dea1-121">Remarks</span></span>

<span data-ttu-id="0dea1-122">Bir bölüm grubu bildirme yapılandırma bölümlerinin için bir kapsayıcı etiket oluşturur ve başka bir kullanıcı tarafından tanımlanan yapılandırma bölümlerinin ile adlandırma çakışmalar olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0dea1-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="0dea1-123">Geçirebilmenize  **\<sectionGroup >** birbirine içindeki öğeler.</span><span class="sxs-lookup"><span data-stu-id="0dea1-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="0dea1-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dea1-124">Example</span></span>

<span data-ttu-id="0dea1-125">Aşağıdaki örnek, bir bölüm grubu bildirme ve bölümler bölüm grubu içinde bildirme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0dea1-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="0dea1-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="0dea1-126">Configuration file</span></span>

<span data-ttu-id="0dea1-127">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="0dea1-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="0dea1-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dea1-128">See also</span></span>

[<span data-ttu-id="0dea1-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="0dea1-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
