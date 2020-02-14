---
title: <clear> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: e8c9b0479bba839a74dff300f0766838b5d99c8d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214831"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="39152-102">\<configSections için > öğesini \<temizleyin ></span><span class="sxs-lookup"><span data-stu-id="39152-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="39152-103">Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.</span><span class="sxs-lookup"><span data-stu-id="39152-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="39152-104">[ **\<yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="39152-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="39152-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="39152-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="39152-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<temizle >**</span><span class="sxs-lookup"><span data-stu-id="39152-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="39152-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39152-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="39152-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39152-108">Attribute</span></span>

|           | <span data-ttu-id="39152-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39152-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="39152-110">**ada**</span><span class="sxs-lookup"><span data-stu-id="39152-110">**name**</span></span>  | <span data-ttu-id="39152-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="39152-111">Required attribute.</span></span><br><br><span data-ttu-id="39152-112">Kaldırılacak bölüm veya bölüm grubunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39152-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="39152-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="39152-113">Parent element</span></span>

|     | <span data-ttu-id="39152-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39152-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="39152-115"> **\<configSections >** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="39152-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="39152-116">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="39152-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="39152-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="39152-117">Child elements</span></span>

<span data-ttu-id="39152-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="39152-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="39152-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39152-119">Remarks</span></span>

<span data-ttu-id="39152-120">**\<clear >** öğesi, geçerli yapılandırma dosyasında daha önce tanımlanan veya yapılandırma dosyası hiyerarşisindeki daha yüksek bir düzeyde bulunan uygulamanızdaki tüm bölümleri ve bölüm gruplarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="39152-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="39152-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="39152-121">Example</span></span>

<span data-ttu-id="39152-122">Bu örnek bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve daha önce makine yapılandırma dosyasında tanımlanan bölümleri temizlemek için bir uygulama yapılandırma dosyasında **\<clear >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="39152-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="39152-123">Aşağıdaki makine yapılandırma dosyası kodu, **\<samplesection >** ve **\<anothersamplesection >** uygulama yapılandırma dosyasından önce okunan iki bölüm bildirir:</span><span class="sxs-lookup"><span data-stu-id="39152-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="39152-124">Aşağıdaki uygulama yapılandırma dosyası kodu, önceden tanımlanmış tüm bölümleri temizler.</span><span class="sxs-lookup"><span data-stu-id="39152-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="39152-125">Uygulama, makine yapılandırma dosyasında belirtilen bölümlerden birindeki ayarları kullanamaz veya alamaz.</span><span class="sxs-lookup"><span data-stu-id="39152-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="39152-126">Ancak, **\<clear >** öğesinden sonra geldiği Için **\<anothersection >** ayarları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="39152-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="39152-127">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="39152-127">Configuration file</span></span>

<span data-ttu-id="39152-128">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39152-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="39152-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39152-129">See also</span></span>

- [<span data-ttu-id="39152-130">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="39152-130">Configuration file schema for the .NET Framework</span></span>](index.md)
