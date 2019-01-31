---
title: <remove> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9ceffd3194c7df41f12ac6cd6b589602965b4920
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279103"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="77738-102">\<kaldırma > öğesi için \<configSections ></span><span class="sxs-lookup"><span data-stu-id="77738-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="77738-103">Önceden tanımlanmış bir bölüm veya bölüm grubu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="77738-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="77738-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="77738-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="77738-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="77738-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="77738-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="77738-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="77738-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77738-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="77738-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="77738-108">Attribute</span></span>

|           | <span data-ttu-id="77738-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77738-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="77738-110">**Adı**</span><span class="sxs-lookup"><span data-stu-id="77738-110">**name**</span></span>  | <span data-ttu-id="77738-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="77738-111">Required attribute.</span></span><br><br><span data-ttu-id="77738-112">Bölüm veya kaldırmak için bölüm grubu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="77738-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="77738-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="77738-113">Parent element</span></span>

|     | <span data-ttu-id="77738-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77738-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="77738-115">**\<configSections >** öğesi</span><span class="sxs-lookup"><span data-stu-id="77738-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="77738-116">Yapılandırma bölümü ve ad alanı bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="77738-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="77738-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="77738-117">Child elements</span></span>

<span data-ttu-id="77738-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="77738-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="77738-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77738-119">Remarks</span></span>

<span data-ttu-id="77738-120">Kullanabileceğiniz  **\<kaldırma >** uygulamanızdan yapılandırma dosyası hiyerarşisindeki daha yüksek düzeyde tanımlanan bölümler ve bölüm grupları'nı kaldırmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="77738-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="77738-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="77738-121">Example</span></span>

<span data-ttu-id="77738-122">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<kaldırma >** makine yapılandırma dosyasında önceden tanımlanmış bir bölümü kaldırmak için bir uygulama yapılandırma dosyasında öğesi.</span><span class="sxs-lookup"><span data-stu-id="77738-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="77738-123">Aşağıdaki makine yapılandırma dosyası kod bölümü bildirir  **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="77738-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="77738-124">Aşağıdaki uygulama yapılandırma dosyası kodu kaldırır  **\<sampleSection >** bölümü.</span><span class="sxs-lookup"><span data-stu-id="77738-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="77738-125">Kaldırma işleminden sonra uygulama ayarlarında alınamıyor  **\<sampleSection >**.</span><span class="sxs-lookup"><span data-stu-id="77738-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="77738-126">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="77738-126">Configuration file</span></span>

<span data-ttu-id="77738-127">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="77738-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="77738-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77738-128">See also</span></span>

- [<span data-ttu-id="77738-129">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="77738-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
