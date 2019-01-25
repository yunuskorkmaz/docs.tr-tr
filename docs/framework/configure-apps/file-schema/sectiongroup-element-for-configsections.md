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
ms.openlocfilehash: 82f89e74d6a09b2c157ff9a273f078e606222f63
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523902"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="d6170-102">\<sectionGroup > öğesi için \<configSections ></span><span class="sxs-lookup"><span data-stu-id="d6170-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="d6170-103">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6170-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="d6170-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d6170-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d6170-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d6170-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="d6170-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="d6170-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d6170-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6170-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="d6170-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d6170-108">Attribute</span></span>

|           | <span data-ttu-id="d6170-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6170-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d6170-110">**Adı**</span><span class="sxs-lookup"><span data-stu-id="d6170-110">**name**</span></span>  | <span data-ttu-id="d6170-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d6170-111">Required attribute.</span></span><br><br><span data-ttu-id="d6170-112">Tanımladığınız bölüm grubu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6170-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d6170-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="d6170-113">Parent element</span></span>

|     | <span data-ttu-id="d6170-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6170-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d6170-115">**\<configSections >** öğesi</span><span class="sxs-lookup"><span data-stu-id="d6170-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="d6170-116">Yapılandırma bölümü ve ad alanı bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="d6170-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d6170-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="d6170-117">Child elements</span></span>

|     | <span data-ttu-id="d6170-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6170-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d6170-119">**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="d6170-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="d6170-120">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="d6170-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d6170-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6170-121">Remarks</span></span>

<span data-ttu-id="d6170-122">Bir bölüm grubu bildirme yapılandırma bölümleri için bir kapsayıcı etiket oluşturur ve başka biri tarafından tanımlanan yapılandırma bölümleri ile hiçbir adlandırma çakışmaları olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6170-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="d6170-123">İç içe yerleştirebilirsiniz  **\<sectionGroup >** öğeleri arasındaki ilişki içinde.</span><span class="sxs-lookup"><span data-stu-id="d6170-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="d6170-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6170-124">Example</span></span>

<span data-ttu-id="d6170-125">Aşağıdaki örnek, bir bölüm grubu bildirmek ve bölümler bölüm grubu içinde bildirmek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d6170-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="d6170-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="d6170-126">Configuration file</span></span>

<span data-ttu-id="d6170-127">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="d6170-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6170-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6170-128">See also</span></span>

- [<span data-ttu-id="d6170-129">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d6170-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
