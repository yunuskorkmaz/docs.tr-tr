---
title: '&lt;Temizle&gt; öğesi için &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bc52e3149c213925ea64a8421ee65befeea4161e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184224"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="bd24b-102">\<Temizle > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="bd24b-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="bd24b-103">Özel uygulama ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="bd24b-103">Clears custom application settings.</span></span>

<span data-ttu-id="bd24b-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bd24b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="bd24b-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="bd24b-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="bd24b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Temizleme >**</span><span class="sxs-lookup"><span data-stu-id="bd24b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bd24b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd24b-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="bd24b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd24b-108">Attributes</span></span>

<span data-ttu-id="bd24b-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd24b-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="bd24b-110">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="bd24b-110">Parent element</span></span>

|     | <span data-ttu-id="bd24b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd24b-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bd24b-112">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="bd24b-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="bd24b-113">Dosya yolları, XML Web hizmeti URL'leri ya da başka bir özel uygulama yapılandırma bilgileri gibi özel uygulama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="bd24b-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="bd24b-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="bd24b-114">Child elements</span></span>

<span data-ttu-id="bd24b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd24b-115">None</span></span>

## <a name="example"></a><span data-ttu-id="bd24b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd24b-116">Example</span></span>

<span data-ttu-id="bd24b-117">Aşağıdaki örnek, özel yapılandırma ayarlarına sıfırlamaya gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bd24b-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="bd24b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd24b-118">See also</span></span>

- [<span data-ttu-id="bd24b-119">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="bd24b-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
