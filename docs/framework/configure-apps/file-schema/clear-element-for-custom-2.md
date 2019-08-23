---
title: <clear>NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: fbb689db4abc5d59729d9a4d9807a02a0983d40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927705"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="3a11a-102">\<NameValueSectionHandler ve DictionarySectionHandler için > öğesini temizle</span><span class="sxs-lookup"><span data-stu-id="3a11a-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="3a11a-103">Bir bölümdeki önceden tanımlanmış tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="3a11a-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="3a11a-104">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3a11a-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="3a11a-105">&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="3a11a-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="3a11a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> Temizle**</span><span class="sxs-lookup"><span data-stu-id="3a11a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3a11a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a11a-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="3a11a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3a11a-108">Attributes</span></span>

<span data-ttu-id="3a11a-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="3a11a-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="3a11a-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="3a11a-110">Parent element</span></span>

|     | <span data-ttu-id="3a11a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a11a-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="3a11a-112">sectionName > öğesi  **\<** </span><span class="sxs-lookup"><span data-stu-id="3a11a-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="3a11a-113"><xref:System.Configuration.NameValueSectionHandler> Ve<xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a11a-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3a11a-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3a11a-114">Child elements</span></span>

<span data-ttu-id="3a11a-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="3a11a-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="3a11a-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a11a-116">Remarks</span></span>

<span data-ttu-id="3a11a-117">Uygulamanızın yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış tüm ayarları kaldırmak için  **\<Clear >** öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a11a-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="3a11a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a11a-118">Example</span></span>

<span data-ttu-id="3a11a-119">Bu örnek bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve daha önce makine yapılandırmasında tanımlanmış bölümleri temizlemek için bir uygulama yapılandırma dosyasında  **\<Clear >** öğesinin nasıl kullanılacağını gösterir dosyasýný.</span><span class="sxs-lookup"><span data-stu-id="3a11a-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="3a11a-120">Aşağıdaki makine yapılandırma dosyası kodu,  **\<MySection >** bölümünü bildirir:</span><span class="sxs-lookup"><span data-stu-id="3a11a-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="3a11a-121">Aşağıdaki uygulama yapılandırma dosyası kodu,  **\<MySection >** 'daki tüm ayarları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3a11a-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="3a11a-122">Uygulama,  **\<makine yapılandırma dosyasının MySection >** bölümünde içinde belirtilen ayarlardan hiçbirini alamıyor.</span><span class="sxs-lookup"><span data-stu-id="3a11a-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="3a11a-123">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="3a11a-123">Configuration file</span></span>

<span data-ttu-id="3a11a-124">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a11a-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a11a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a11a-125">See also</span></span>

- [<span data-ttu-id="3a11a-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="3a11a-126">Configuration file schema for the .NET Framework</span></span>](index.md)
