---
description: 'Hakkında daha fazla bilgi edinin: <remove> NameValueSectionHandler ve DictionarySectionHandler için öğesi'
title: <remove> NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: bf1434b257aa014c8f46e34f2d57d109bd510452
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740086"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="67577-103">\<remove> NameValueSectionHandler ve DictionarySectionHandler için öğesi</span><span class="sxs-lookup"><span data-stu-id="67577-103">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="67577-104">Daha önce tanımlanmış bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="67577-104">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="67577-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="67577-105">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="67577-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="67577-106">Attribute</span></span>

|           | <span data-ttu-id="67577-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67577-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="67577-108">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="67577-108">**key**</span></span>   | <span data-ttu-id="67577-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="67577-109">Required attribute.</span></span><br><br><span data-ttu-id="67577-110">Kaldırılacak ayarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="67577-110">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="67577-111">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="67577-111">Parent element</span></span>

| <span data-ttu-id="67577-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="67577-112">Element</span></span> | <span data-ttu-id="67577-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67577-113">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="67577-114">**\<sectionName>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="67577-114">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="67577-115">Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> .</span><span class="sxs-lookup"><span data-stu-id="67577-115">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="67577-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="67577-116">Child elements</span></span>

<span data-ttu-id="67577-117">Yok</span><span class="sxs-lookup"><span data-stu-id="67577-117">None</span></span>

## <a name="remarks"></a><span data-ttu-id="67577-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67577-118">Remarks</span></span>

<span data-ttu-id="67577-119">**\<remove>** Uygulamanızı yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan ayarları kaldırabilmeniz için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67577-119">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="67577-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="67577-120">Example</span></span>

<span data-ttu-id="67577-121">Aşağıdaki örnek, **\<remove>** daha önce makine yapılandırma dosyasında tanımlanan ayarları kaldırmak için bir uygulama yapılandırma dosyasında öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="67577-121">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="67577-122">Aşağıdaki makine yapılandırma dosyası kodu, bölümünü bildirir **\<mySection>** ve iki ayar ekler `key1` `key2` :</span><span class="sxs-lookup"><span data-stu-id="67577-122">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="67577-123">Aşağıdaki uygulama yapılandırma dosyası kodu, bu `key2` ayarı öğesinden kaldırır **\<mySection>** :</span><span class="sxs-lookup"><span data-stu-id="67577-123">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="67577-124">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="67577-124">Configuration file</span></span>

<span data-ttu-id="67577-125">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67577-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="67577-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67577-126">See also</span></span>

- [<span data-ttu-id="67577-127">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="67577-127">Configuration file schema for the .NET Framework</span></span>](index.md)
