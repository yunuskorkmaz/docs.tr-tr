---
title: "&lt;ekleme&gt; öğesi için &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b00af6f7d735d5db8fd746205ba225253cad133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="b8b4a-102">\<Ekle > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="b8b4a-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="b8b4a-103">Özel uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-103">Adds a custom application setting.</span></span>

<span data-ttu-id="b8b4a-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b8b4a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="b8b4a-105">&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="b8b4a-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="b8b4a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="b8b4a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b8b4a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8b4a-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="b8b4a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8b4a-108">Attributes</span></span>

|           | <span data-ttu-id="b8b4a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8b4a-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="b8b4a-110">**anahtarı**</span><span class="sxs-lookup"><span data-stu-id="b8b4a-110">**key**</span></span>   | <span data-ttu-id="b8b4a-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-111">Required attribute.</span></span><br><br><span data-ttu-id="b8b4a-112">Eklenecek anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="b8b4a-113">**değer**</span><span class="sxs-lookup"><span data-stu-id="b8b4a-113">**value**</span></span> | <span data-ttu-id="b8b4a-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-114">Required attribute.</span></span><br><br><span data-ttu-id="b8b4a-115">Eklenecek anahtar değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="b8b4a-116">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="b8b4a-116">Parent element</span></span>

|     | <span data-ttu-id="b8b4a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8b4a-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b8b4a-118">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="b8b4a-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="b8b4a-119">Dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgilerini bir uygulama gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b8b4a-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b8b4a-120">Child elements</span></span>

<span data-ttu-id="b8b4a-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-121">None</span></span>

## <a name="example"></a><span data-ttu-id="b8b4a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b4a-122">Example</span></span>

<span data-ttu-id="b8b4a-123">Aşağıdaki örnekte uygulamanın adı için bir özel yapılandırma ayarı ekleme gösterir:</span><span class="sxs-lookup"><span data-stu-id="b8b4a-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="b8b4a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8b4a-124">See also</span></span>

[<span data-ttu-id="b8b4a-125">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="b8b4a-125">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
