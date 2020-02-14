---
title: <sectionGroup> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: eb221027470fe6e485f8fcc4b939b71e4f219712
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215256"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="e65c5-102">\<configSections için sectionGroup > öğesi \<></span><span class="sxs-lookup"><span data-stu-id="e65c5-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="e65c5-103">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e65c5-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="e65c5-104">[ **\<yapılandırma >** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e65c5-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="e65c5-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="e65c5-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="e65c5-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="e65c5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e65c5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e65c5-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="e65c5-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e65c5-108">Attribute</span></span>

|           | <span data-ttu-id="e65c5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e65c5-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="e65c5-110">**ada**</span><span class="sxs-lookup"><span data-stu-id="e65c5-110">**name**</span></span>  | <span data-ttu-id="e65c5-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e65c5-111">Required attribute.</span></span><br><br><span data-ttu-id="e65c5-112">Tanımladığınız bölüm grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e65c5-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="e65c5-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="e65c5-113">Parent element</span></span>

|     | <span data-ttu-id="e65c5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e65c5-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e65c5-115"> **\<configSections >** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="e65c5-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="e65c5-116">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e65c5-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e65c5-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e65c5-117">Child elements</span></span>

|     | <span data-ttu-id="e65c5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e65c5-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e65c5-119"> **\<Bölüm >** </span><span class="sxs-lookup"><span data-stu-id="e65c5-119">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="e65c5-120">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="e65c5-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e65c5-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e65c5-121">Remarks</span></span>

<span data-ttu-id="e65c5-122">Bölüm grubunu bildirmek, yapılandırma bölümleri için bir kapsayıcı etiketi oluşturur ve başka biri tarafından tanımlanan yapılandırma bölümleriyle adlandırma çakışması olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e65c5-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="e65c5-123">**\<sectionGroup >** öğelerini birbirine iç içe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e65c5-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="e65c5-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e65c5-124">Example</span></span>

<span data-ttu-id="e65c5-125">Aşağıdaki örnek, bir bölüm grubunun nasıl bildirilemeyeceğini ve bölüm grubu içinde bölümlerin nasıl bildirilemeyeceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e65c5-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="e65c5-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="e65c5-126">Configuration file</span></span>

<span data-ttu-id="e65c5-127">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e65c5-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e65c5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e65c5-128">See also</span></span>

- [<span data-ttu-id="e65c5-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e65c5-129">Configuration file schema for the .NET Framework</span></span>](index.md)
