---
title: <sectionGroup> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ce0fa5bd77a7b9012d69fd5afab1f4c332f213a7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276139"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="f837e-102">\<sectionGroup > öğesi için \<configSections ></span><span class="sxs-lookup"><span data-stu-id="f837e-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="f837e-103">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f837e-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="f837e-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f837e-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f837e-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f837e-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f837e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="f837e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f837e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f837e-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="f837e-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f837e-108">Attribute</span></span>

|           | <span data-ttu-id="f837e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f837e-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f837e-110">**Adı**</span><span class="sxs-lookup"><span data-stu-id="f837e-110">**name**</span></span>  | <span data-ttu-id="f837e-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f837e-111">Required attribute.</span></span><br><br><span data-ttu-id="f837e-112">Tanımladığınız bölüm grubu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f837e-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f837e-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="f837e-113">Parent element</span></span>

|     | <span data-ttu-id="f837e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f837e-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f837e-115">**\<configSections >** öğesi</span><span class="sxs-lookup"><span data-stu-id="f837e-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="f837e-116">Yapılandırma bölümü ve ad alanı bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f837e-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f837e-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f837e-117">Child elements</span></span>

|     | <span data-ttu-id="f837e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f837e-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f837e-119">**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="f837e-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="f837e-120">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f837e-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f837e-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f837e-121">Remarks</span></span>

<span data-ttu-id="f837e-122">Bir bölüm grubu bildirme yapılandırma bölümleri için bir kapsayıcı etiket oluşturur ve başka biri tarafından tanımlanan yapılandırma bölümleri ile hiçbir adlandırma çakışmaları olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f837e-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="f837e-123">İç içe yerleştirebilirsiniz  **\<sectionGroup >** öğeleri arasındaki ilişki içinde.</span><span class="sxs-lookup"><span data-stu-id="f837e-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="f837e-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f837e-124">Example</span></span>

<span data-ttu-id="f837e-125">Aşağıdaki örnek, bir bölüm grubu bildirmek ve bölümler bölüm grubu içinde bildirmek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f837e-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="f837e-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="f837e-126">Configuration file</span></span>

<span data-ttu-id="f837e-127">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="f837e-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f837e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f837e-128">See also</span></span>

- [<span data-ttu-id="f837e-129">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="f837e-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
