---
title: '&lt;ekleme&gt; öğesi için &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 35a9fc08033d2b9cd1dae5a1f1f3ddcd361f03eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="324f6-102">\<Ekle > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="324f6-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="324f6-103">Özel uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="324f6-103">Adds a custom application setting.</span></span>

<span data-ttu-id="324f6-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="324f6-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="324f6-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="324f6-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="324f6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="324f6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="324f6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="324f6-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="324f6-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="324f6-108">Attributes</span></span>

|           | <span data-ttu-id="324f6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="324f6-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="324f6-110">**Anahtarı**</span><span class="sxs-lookup"><span data-stu-id="324f6-110">**key**</span></span>   | <span data-ttu-id="324f6-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="324f6-111">Required attribute.</span></span><br><br><span data-ttu-id="324f6-112">Eklenecek anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="324f6-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="324f6-113">**value**</span><span class="sxs-lookup"><span data-stu-id="324f6-113">**value**</span></span> | <span data-ttu-id="324f6-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="324f6-114">Required attribute.</span></span><br><br><span data-ttu-id="324f6-115">Eklenecek anahtar değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="324f6-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="324f6-116">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="324f6-116">Parent element</span></span>

|     | <span data-ttu-id="324f6-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="324f6-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="324f6-118">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="324f6-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="324f6-119">Dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgilerini bir uygulama gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="324f6-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="324f6-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="324f6-120">Child elements</span></span>

<span data-ttu-id="324f6-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="324f6-121">None</span></span>

## <a name="example"></a><span data-ttu-id="324f6-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="324f6-122">Example</span></span>

<span data-ttu-id="324f6-123">Aşağıdaki örnekte uygulamanın adı için bir özel yapılandırma ayarı ekleme gösterir:</span><span class="sxs-lookup"><span data-stu-id="324f6-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="324f6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="324f6-124">See also</span></span>

[<span data-ttu-id="324f6-125">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="324f6-125">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
