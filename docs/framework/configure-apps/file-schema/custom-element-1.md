---
title: SingleTagSectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "80635395"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="07eb8-102">SingleTagSectionHandler için özel öğe</span><span class="sxs-lookup"><span data-stu-id="07eb8-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="07eb8-103">, Bir öğesi tarafından tanımlanan \<section> ve sınıfını kullanan özel bir yapılandırma bölümünde ayarları tanımlar <xref:System.Configuration.SingleTagSectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="07eb8-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="07eb8-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="07eb8-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="07eb8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07eb8-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="07eb8-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="07eb8-106">Attributes</span></span>

<span data-ttu-id="07eb8-107">Öznitelikler ve öznitelik değerleri Kullanıcı tanımlı ' dır.</span><span class="sxs-lookup"><span data-stu-id="07eb8-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="07eb8-108">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="07eb8-108">Parent element</span></span>

|     | <span data-ttu-id="07eb8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07eb8-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="07eb8-110">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="07eb8-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="07eb8-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="07eb8-111">Child elements</span></span>

<span data-ttu-id="07eb8-112">Yok</span><span class="sxs-lookup"><span data-stu-id="07eb8-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="07eb8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07eb8-113">Remarks</span></span>

<span data-ttu-id="07eb8-114">**\<sectionName>** Öğesi, öğesinde bir etiketi tarafından tanımlanan özel bir öğedir [**\<section>**](section-element.md) [**\<configSections>**](configsections-element-for-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="07eb8-114">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="07eb8-115">Yapılandırma sistemi, çağırdığınızda bir <xref:System.Collections.IDictionary> nesne döndürür <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="07eb8-115">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="07eb8-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="07eb8-116">Example</span></span>

<span data-ttu-id="07eb8-117">Aşağıdaki örnek, **\<sampleSection>** sınıfı tarafından okunan ayarları içeren adlı özel bir öğe bildirir <xref:System.Configuration.SingleTagSectionHandler> :</span><span class="sxs-lookup"><span data-stu-id="07eb8-117">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="07eb8-118">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="07eb8-118">Configuration file</span></span>

<span data-ttu-id="07eb8-119">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="07eb8-119">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="07eb8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07eb8-120">See also</span></span>

- [<span data-ttu-id="07eb8-121">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="07eb8-121">Configuration file schema for the .NET Framework</span></span>](index.md)
