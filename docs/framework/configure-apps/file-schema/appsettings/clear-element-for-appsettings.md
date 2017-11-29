---
title: "&lt;Clear&gt; öğesi için &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ac1e9a86d0c3e1bb1f23b753fd9867effef03ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="30d27-102">\<Clear > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="30d27-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="30d27-103">Özel uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="30d27-103">Clears custom application settings.</span></span>

<span data-ttu-id="30d27-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="30d27-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="30d27-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="30d27-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="30d27-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="30d27-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="30d27-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30d27-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="30d27-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="30d27-108">Attributes</span></span>

<span data-ttu-id="30d27-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="30d27-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="30d27-110">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="30d27-110">Parent element</span></span>

|     | <span data-ttu-id="30d27-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30d27-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="30d27-112">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="30d27-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="30d27-113">Dosya yolları, XML Web hizmeti URL'leri veya başka bir özel uygulama yapılandırma bilgilerini gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="30d27-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="30d27-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="30d27-114">Child elements</span></span>

<span data-ttu-id="30d27-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="30d27-115">None</span></span>

## <a name="example"></a><span data-ttu-id="30d27-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="30d27-116">Example</span></span>

<span data-ttu-id="30d27-117">Aşağıdaki örnek, özel yapılandırma ayarlarına sıfırlamaya gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="30d27-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="30d27-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30d27-118">See also</span></span>

[<span data-ttu-id="30d27-119">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="30d27-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
