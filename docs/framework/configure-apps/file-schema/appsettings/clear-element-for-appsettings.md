---
title: '&lt;Clear&gt; öğesi için &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 525818309ddc142fdb3ad65ce841ea58c1d635a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350672"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="17aa3-102">\<Clear > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="17aa3-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="17aa3-103">Özel uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="17aa3-103">Clears custom application settings.</span></span>

<span data-ttu-id="17aa3-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="17aa3-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="17aa3-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="17aa3-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="17aa3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="17aa3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="17aa3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17aa3-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="17aa3-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="17aa3-108">Attributes</span></span>

<span data-ttu-id="17aa3-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="17aa3-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="17aa3-110">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="17aa3-110">Parent element</span></span>

|     | <span data-ttu-id="17aa3-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17aa3-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="17aa3-112">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="17aa3-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="17aa3-113">Dosya yolları, XML Web hizmeti URL'leri veya başka bir özel uygulama yapılandırma bilgilerini gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="17aa3-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="17aa3-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="17aa3-114">Child elements</span></span>

<span data-ttu-id="17aa3-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="17aa3-115">None</span></span>

## <a name="example"></a><span data-ttu-id="17aa3-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="17aa3-116">Example</span></span>

<span data-ttu-id="17aa3-117">Aşağıdaki örnek, özel yapılandırma ayarlarına sıfırlamaya gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="17aa3-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="17aa3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17aa3-118">See also</span></span>

[<span data-ttu-id="17aa3-119">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="17aa3-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
