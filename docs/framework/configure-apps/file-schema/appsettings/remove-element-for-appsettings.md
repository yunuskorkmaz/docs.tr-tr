---
title: "&lt;kaldırma&gt; öğesi için &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e803561ef20bb17ed7c637eb487027466b65077
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="6cfbb-102">\<kaldırma > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="6cfbb-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="6cfbb-103">Özel uygulama ayarlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6cfbb-103">Removes custom application settings.</span></span>

<span data-ttu-id="6cfbb-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6cfbb-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="6cfbb-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="6cfbb-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="6cfbb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="6cfbb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6cfbb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cfbb-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="6cfbb-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6cfbb-108">Attribute</span></span>

|         | <span data-ttu-id="6cfbb-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cfbb-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="6cfbb-110">**anahtarı**</span><span class="sxs-lookup"><span data-stu-id="6cfbb-110">**key**</span></span> | <span data-ttu-id="6cfbb-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6cfbb-111">Required attribute.</span></span><br><br><span data-ttu-id="6cfbb-112">Kaldırılacak anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6cfbb-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="6cfbb-113">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="6cfbb-113">Parent element</span></span>

|     | <span data-ttu-id="6cfbb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cfbb-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6cfbb-115">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="6cfbb-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="6cfbb-116">Dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgilerini bir uygulama gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6cfbb-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6cfbb-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6cfbb-117">Child elements</span></span>

<span data-ttu-id="6cfbb-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="6cfbb-118">None</span></span>

## <a name="example"></a><span data-ttu-id="6cfbb-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cfbb-119">Example</span></span>

<span data-ttu-id="6cfbb-120">Aşağıdaki örnekte bir özel yapılandırma ayarını kaldırın gösterilmektedir `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="6cfbb-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="6cfbb-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cfbb-121">See also</span></span>

[<span data-ttu-id="6cfbb-122">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6cfbb-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
