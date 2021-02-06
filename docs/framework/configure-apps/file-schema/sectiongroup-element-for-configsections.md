---
description: 'İçin: öğesi hakkında daha fazla bilgi <sectionGroup><configSections>'
title: <configSections> için <sectionGroup> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: 0d822b98acbc041b9d6e146e9cd15848a73d2f88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639893"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="fe077-103">\<configSections> için \<sectionGroup> öğesi</span><span class="sxs-lookup"><span data-stu-id="fe077-103">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="fe077-104">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe077-104">Defines a namespace for configuration sections.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a><span data-ttu-id="fe077-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe077-105">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="fe077-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fe077-106">Attribute</span></span>

|           | <span data-ttu-id="fe077-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe077-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="fe077-108">**ada**</span><span class="sxs-lookup"><span data-stu-id="fe077-108">**name**</span></span>  | <span data-ttu-id="fe077-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fe077-109">Required attribute.</span></span><br><br><span data-ttu-id="fe077-110">Tanımladığınız bölüm grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe077-110">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="fe077-111">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="fe077-111">Parent element</span></span>

|     | <span data-ttu-id="fe077-112">Description</span><span class="sxs-lookup"><span data-stu-id="fe077-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fe077-113">**\<configSections>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="fe077-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="fe077-114">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe077-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="fe077-115">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fe077-115">Child elements</span></span>

|     | <span data-ttu-id="fe077-116">Description</span><span class="sxs-lookup"><span data-stu-id="fe077-116">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="fe077-117">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="fe077-117">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="fe077-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe077-118">Remarks</span></span>

<span data-ttu-id="fe077-119">Bölüm grubunu bildirmek, yapılandırma bölümleri için bir kapsayıcı etiketi oluşturur ve başka biri tarafından tanımlanan yapılandırma bölümleriyle adlandırma çakışması olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe077-119">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="fe077-120">Öğeleri birbirlerine iç içe yerleştirebilirsiniz **\<sectionGroup>** .</span><span class="sxs-lookup"><span data-stu-id="fe077-120">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="fe077-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe077-121">Example</span></span>

<span data-ttu-id="fe077-122">Aşağıdaki örnek, bir bölüm grubunun nasıl bildirilemeyeceğini ve bölüm grubu içinde bölümlerin nasıl bildirilemeyeceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="fe077-122">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="fe077-123">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="fe077-123">Configuration file</span></span>

<span data-ttu-id="fe077-124">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe077-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe077-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe077-125">See also</span></span>

- [<span data-ttu-id="fe077-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="fe077-126">Configuration file schema for the .NET Framework</span></span>](index.md)
