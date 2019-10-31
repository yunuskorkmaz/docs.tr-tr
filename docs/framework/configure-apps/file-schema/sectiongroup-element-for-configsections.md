---
title: <configSections> için <sectionGroup> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9113811557ded3a580a0bbacb24f2fe7e8d05ccf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114777"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="f1181-102">\<configSections için sectionGroup > öğesi \<</span><span class="sxs-lookup"><span data-stu-id="f1181-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="f1181-103">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f1181-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="f1181-104">[ **\<yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f1181-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="f1181-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f1181-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f1181-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="f1181-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f1181-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1181-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="f1181-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f1181-108">Attribute</span></span>

|           | <span data-ttu-id="f1181-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1181-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f1181-110">**ada**</span><span class="sxs-lookup"><span data-stu-id="f1181-110">**name**</span></span>  | <span data-ttu-id="f1181-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f1181-111">Required attribute.</span></span><br><br><span data-ttu-id="f1181-112">Tanımladığınız bölüm grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1181-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f1181-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="f1181-113">Parent element</span></span>

|     | <span data-ttu-id="f1181-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1181-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f1181-115"> **\<configSections >** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="f1181-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="f1181-116">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f1181-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f1181-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f1181-117">Child elements</span></span>

|     | <span data-ttu-id="f1181-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1181-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f1181-119"> **\<Bölüm >** </span><span class="sxs-lookup"><span data-stu-id="f1181-119">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="f1181-120">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f1181-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f1181-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1181-121">Remarks</span></span>

<span data-ttu-id="f1181-122">Bölüm grubunu bildirmek, yapılandırma bölümleri için bir kapsayıcı etiketi oluşturur ve başka biri tarafından tanımlanan yapılandırma bölümleriyle adlandırma çakışması olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1181-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="f1181-123">**\<sectionGroup >** öğelerini birbirine iç içe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1181-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="f1181-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1181-124">Example</span></span>

<span data-ttu-id="f1181-125">Aşağıdaki örnek, bir bölüm grubunun nasıl bildirilemeyeceğini ve bölüm grubu içinde bölümlerin nasıl bildirilemeyeceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f1181-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="f1181-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="f1181-126">Configuration file</span></span>

<span data-ttu-id="f1181-127">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f1181-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1181-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1181-128">See also</span></span>

- [<span data-ttu-id="f1181-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="f1181-129">Configuration file schema for the .NET Framework</span></span>](index.md)
