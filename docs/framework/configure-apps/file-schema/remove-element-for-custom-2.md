---
title: <remove>NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd338ff2d613be31ab1524f6baed6107f803a688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920942"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="bab6d-102">\<NameValueSectionHandler ve DictionarySectionHandler için > öğesini kaldırın</span><span class="sxs-lookup"><span data-stu-id="bab6d-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="bab6d-103">Daha önce tanımlanmış bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bab6d-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="bab6d-104">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bab6d-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="bab6d-105">&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="bab6d-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="bab6d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> Kaldır**</span><span class="sxs-lookup"><span data-stu-id="bab6d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bab6d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bab6d-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="bab6d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bab6d-108">Attribute</span></span>

|           | <span data-ttu-id="bab6d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bab6d-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="bab6d-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="bab6d-110">**key**</span></span>   | <span data-ttu-id="bab6d-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bab6d-111">Required attribute.</span></span><br><br><span data-ttu-id="bab6d-112">Kaldırılacak ayarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bab6d-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="bab6d-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="bab6d-113">Parent element</span></span>

| <span data-ttu-id="bab6d-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="bab6d-114">Element</span></span> | <span data-ttu-id="bab6d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bab6d-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="bab6d-116">sectionName > öğesi  **\<** </span><span class="sxs-lookup"><span data-stu-id="bab6d-116">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="bab6d-117"><xref:System.Configuration.NameValueSectionHandler> Ve<xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bab6d-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="bab6d-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="bab6d-118">Child elements</span></span>

<span data-ttu-id="bab6d-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="bab6d-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="bab6d-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bab6d-120">Remarks</span></span>

<span data-ttu-id="bab6d-121">Uygulama yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan ayarları kaldırabilmeniz için  **\<Remove >** öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bab6d-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="bab6d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="bab6d-122">Example</span></span>

<span data-ttu-id="bab6d-123">Aşağıdaki örnek, makine yapılandırma dosyasında daha önce tanımlanan ayarları kaldırmak için bir uygulama yapılandırma dosyasında  **\<Remove >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bab6d-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="bab6d-124">Aşağıdaki makine yapılandırma dosyası kodu,  **\<MySection >** bölümünü bildirir ve `key2`iki ayar `key1` ekler:</span><span class="sxs-lookup"><span data-stu-id="bab6d-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="bab6d-125">Aşağıdaki uygulama yapılandırma dosyası kodu, `key2`  **\<MySection >** ayarını kaldırır:</span><span class="sxs-lookup"><span data-stu-id="bab6d-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="bab6d-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="bab6d-126">Configuration file</span></span>

<span data-ttu-id="bab6d-127">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bab6d-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="bab6d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bab6d-128">See also</span></span>

- [<span data-ttu-id="bab6d-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="bab6d-129">Configuration file schema for the .NET Framework</span></span>](index.md)
