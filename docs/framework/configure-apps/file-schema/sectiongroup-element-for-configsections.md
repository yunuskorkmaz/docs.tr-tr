---
title: <configSections> için <sectionGroup> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: eb221027470fe6e485f8fcc4b939b71e4f219712
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215256"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="dafda-102">\<configSections> için \<sectionGroup> öğesi</span><span class="sxs-lookup"><span data-stu-id="dafda-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="dafda-103">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dafda-103">Defines a namespace for configuration sections.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a><span data-ttu-id="dafda-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dafda-104">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="dafda-105">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dafda-105">Attribute</span></span>

|           | <span data-ttu-id="dafda-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dafda-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="dafda-107">**ada**</span><span class="sxs-lookup"><span data-stu-id="dafda-107">**name**</span></span>  | <span data-ttu-id="dafda-108">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="dafda-108">Required attribute.</span></span><br><br><span data-ttu-id="dafda-109">Tanımladığınız bölüm grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dafda-109">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="dafda-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="dafda-110">Parent element</span></span>

|     | <span data-ttu-id="dafda-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dafda-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="dafda-112">**\<configSections>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="dafda-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="dafda-113">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dafda-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="dafda-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="dafda-114">Child elements</span></span>

|     | <span data-ttu-id="dafda-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dafda-115">Description</span></span> |
| --- | ----------- |
| [**\<section>**](section-element.md) | <span data-ttu-id="dafda-116">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="dafda-116">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="dafda-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dafda-117">Remarks</span></span>

<span data-ttu-id="dafda-118">Bölüm grubunu bildirmek, yapılandırma bölümleri için bir kapsayıcı etiketi oluşturur ve başka biri tarafından tanımlanan yapılandırma bölümleriyle adlandırma çakışması olmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dafda-118">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="dafda-119">Öğeleri birbirlerine iç içe yerleştirebilirsiniz **\<sectionGroup>** .</span><span class="sxs-lookup"><span data-stu-id="dafda-119">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="dafda-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="dafda-120">Example</span></span>

<span data-ttu-id="dafda-121">Aşağıdaki örnek, bir bölüm grubunun nasıl bildirilemeyeceğini ve bölüm grubu içinde bölümlerin nasıl bildirilemeyeceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="dafda-121">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="dafda-122">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="dafda-122">Configuration file</span></span>

<span data-ttu-id="dafda-123">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dafda-123">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="dafda-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dafda-124">See also</span></span>

- [<span data-ttu-id="dafda-125">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="dafda-125">Configuration file schema for the .NET Framework</span></span>](index.md)
