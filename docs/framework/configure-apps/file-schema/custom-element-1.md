---
description: 'Daha fazla bilgi edinin: SingleTagSectionHandler için özel öğe'
title: SingleTagSectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 83022a1ebf295b89d5f868589e3d9a77c78e3fab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729985"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="ccfac-103">SingleTagSectionHandler için özel öğe</span><span class="sxs-lookup"><span data-stu-id="ccfac-103">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="ccfac-104">, Bir öğesi tarafından tanımlanan \<section> ve sınıfını kullanan özel bir yapılandırma bölümünde ayarları tanımlar <xref:System.Configuration.SingleTagSectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="ccfac-104">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="ccfac-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="ccfac-105">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="ccfac-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ccfac-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="ccfac-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ccfac-107">Attributes</span></span>

<span data-ttu-id="ccfac-108">Öznitelikler ve öznitelik değerleri Kullanıcı tanımlı ' dır.</span><span class="sxs-lookup"><span data-stu-id="ccfac-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="ccfac-109">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="ccfac-109">Parent element</span></span>

|     | <span data-ttu-id="ccfac-110">Description</span><span class="sxs-lookup"><span data-stu-id="ccfac-110">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="ccfac-111">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ccfac-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ccfac-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ccfac-112">Child elements</span></span>

<span data-ttu-id="ccfac-113">Yok</span><span class="sxs-lookup"><span data-stu-id="ccfac-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="ccfac-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ccfac-114">Remarks</span></span>

<span data-ttu-id="ccfac-115">**\<sectionName>** Öğesi, öğesinde bir etiketi tarafından tanımlanan özel bir öğedir [**\<section>**](section-element.md) [**\<configSections>**](configsections-element-for-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="ccfac-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="ccfac-116">Yapılandırma sistemi, çağırdığınızda bir <xref:System.Collections.IDictionary> nesne döndürür <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ccfac-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="ccfac-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="ccfac-117">Example</span></span>

<span data-ttu-id="ccfac-118">Aşağıdaki örnek, **\<sampleSection>** sınıfı tarafından okunan ayarları içeren adlı özel bir öğe bildirir <xref:System.Configuration.SingleTagSectionHandler> :</span><span class="sxs-lookup"><span data-stu-id="ccfac-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="ccfac-119">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="ccfac-119">Configuration file</span></span>

<span data-ttu-id="ccfac-120">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan dosyaları *Web.config* kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ccfac-120">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccfac-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccfac-121">See also</span></span>

- [<span data-ttu-id="ccfac-122">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ccfac-122">Configuration file schema for the .NET Framework</span></span>](index.md)
