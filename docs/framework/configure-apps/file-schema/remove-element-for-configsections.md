---
title: '&lt;kaldırma&gt; öğesi için &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 6555981edeb6f7f088fb12c710d0146cf58d5be1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752422"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="20cf7-102">\<kaldırma > öğesi için \<configSections ></span><span class="sxs-lookup"><span data-stu-id="20cf7-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="20cf7-103">Önceden tanımlanmış bölüm veya bölüm grubu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="20cf7-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="20cf7-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="20cf7-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="20cf7-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="20cf7-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="20cf7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="20cf7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="20cf7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20cf7-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="20cf7-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20cf7-108">Attribute</span></span>

|           | <span data-ttu-id="20cf7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20cf7-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="20cf7-110">**Adı**</span><span class="sxs-lookup"><span data-stu-id="20cf7-110">**name**</span></span>  | <span data-ttu-id="20cf7-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="20cf7-111">Required attribute.</span></span><br><br><span data-ttu-id="20cf7-112">Bölüm veya kaldırmak için bölüm grubu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="20cf7-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="20cf7-113">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="20cf7-113">Parent element</span></span>

|     | <span data-ttu-id="20cf7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20cf7-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="20cf7-115">**\<configSections >** öğesi</span><span class="sxs-lookup"><span data-stu-id="20cf7-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="20cf7-116">Yapılandırma bölümü ve ad alanı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="20cf7-116">Contains configuration section and namespace declarations.</span></span> |

# <a name="child-elements"></a><span data-ttu-id="20cf7-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="20cf7-117">Child elements</span></span>

<span data-ttu-id="20cf7-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="20cf7-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="20cf7-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20cf7-119">Remarks</span></span>

<span data-ttu-id="20cf7-120">Kullanabileceğiniz  **\<kaldırma >** öğesi yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanan uygulamanızı bölümler ve bölüm grupları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="20cf7-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="20cf7-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="20cf7-121">Example</span></span>

<span data-ttu-id="20cf7-122">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<kaldırma >** makine yapılandırma dosyasında önceden tanımlanmış bir bölümü kaldırmak için bir uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="20cf7-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="20cf7-123">Bölümü aşağıdaki makine yapılandırma dosyası kodu bildirir  **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="20cf7-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="20cf7-124">Aşağıdaki uygulama yapılandırma dosyası kodu kaldırır  **\<sampleSection >** bölümü.</span><span class="sxs-lookup"><span data-stu-id="20cf7-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="20cf7-125">Kaldırıldıktan sonra uygulama ayarlarında alınamıyor  **\<sampleSection >**.</span><span class="sxs-lookup"><span data-stu-id="20cf7-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="20cf7-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="20cf7-126">Configuration file</span></span>

<span data-ttu-id="20cf7-127">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="20cf7-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="20cf7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20cf7-128">See also</span></span>

[<span data-ttu-id="20cf7-129">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="20cf7-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
