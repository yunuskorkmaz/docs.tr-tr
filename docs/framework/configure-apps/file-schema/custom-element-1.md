---
title: SingleTagSectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635395"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="16c40-102">SingleTagSectionHandler için özel öğe</span><span class="sxs-lookup"><span data-stu-id="16c40-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="16c40-103">Bir bölüm> öğesi tarafından tanımlanan ve \< <xref:System.Configuration.SingleTagSectionHandler> sınıfı kullanan özel bir yapılandırma bölümündeki ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="16c40-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="16c40-104">yapılandırma &nbsp; &nbsp;>[\*\* \<\*\*](configuration-element.md) \* \<bölümName>\*</span><span class="sxs-lookup"><span data-stu-id="16c40-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="16c40-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16c40-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="16c40-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="16c40-106">Attributes</span></span>

<span data-ttu-id="16c40-107">Öznitelikler ve öznitelik değerleri kullanıcı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="16c40-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="16c40-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="16c40-108">Parent element</span></span>

|     | <span data-ttu-id="16c40-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16c40-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="16c40-110">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="16c40-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="16c40-111">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="16c40-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="16c40-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="16c40-112">Child elements</span></span>

<span data-ttu-id="16c40-113">None</span><span class="sxs-lookup"><span data-stu-id="16c40-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="16c40-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16c40-114">Remarks</span></span>

<span data-ttu-id="16c40-115">sectionName>[\*\* \<öğesi, configSections>\*\*](configsections-element-for-configuration.md) öğesindeki bir [\*\* \<bölüm>\*\*](section-element.md) etiketiyle tanımlanan özel bir öğedir. \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="16c40-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="16c40-116">Yapılandırma sistemi, <xref:System.Collections.IDictionary> <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16c40-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="16c40-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="16c40-117">Example</span></span>

<span data-ttu-id="16c40-118">Aşağıdaki örnek, <xref:System.Configuration.SingleTagSectionHandler> sınıf tarafından okunan ayarları içeren \*\* \<örnekBölüm>\*\* adlı özel bir öğe bildirir:</span><span class="sxs-lookup"><span data-stu-id="16c40-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="16c40-119">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="16c40-119">Configuration file</span></span>

<span data-ttu-id="16c40-120">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16c40-120">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="16c40-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16c40-121">See also</span></span>

- [<span data-ttu-id="16c40-122">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="16c40-122">Configuration file schema for the .NET Framework</span></span>](index.md)
