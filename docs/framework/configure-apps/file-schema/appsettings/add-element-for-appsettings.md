---
title: <appSettings> için <add> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 594ba4f289012e775e93acba98056b60bdd94cbd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927742"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="29e58-102">\<appSettings için \<> öğesi ekleme ></span><span class="sxs-lookup"><span data-stu-id="29e58-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="29e58-103">Özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="29e58-103">Adds a custom application setting.</span></span>

<span data-ttu-id="29e58-104">[ **\<Yapılandırma >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="29e58-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="29e58-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="29e58-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="29e58-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="29e58-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="29e58-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29e58-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="29e58-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29e58-108">Attributes</span></span>

|           | <span data-ttu-id="29e58-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29e58-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="29e58-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="29e58-110">**key**</span></span>   | <span data-ttu-id="29e58-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="29e58-111">Required attribute.</span></span><br><br><span data-ttu-id="29e58-112">Eklenecek anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29e58-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="29e58-113">**value**</span><span class="sxs-lookup"><span data-stu-id="29e58-113">**value**</span></span> | <span data-ttu-id="29e58-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="29e58-114">Required attribute.</span></span><br><br><span data-ttu-id="29e58-115">Eklenecek anahtarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="29e58-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="29e58-116">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="29e58-116">Parent element</span></span>

|     | <span data-ttu-id="29e58-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29e58-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="29e58-118"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="29e58-118">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="29e58-119">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="29e58-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="29e58-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="29e58-120">Child elements</span></span>

<span data-ttu-id="29e58-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="29e58-121">None</span></span>

## <a name="example"></a><span data-ttu-id="29e58-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="29e58-122">Example</span></span>

<span data-ttu-id="29e58-123">Aşağıdaki örnek, uygulamanın adı için nasıl özel bir yapılandırma ayarı ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="29e58-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="29e58-124">Aşağıdaki örnek, `<add>` bir ASP.NET uygulamasında iki uyumluluk ayarı tanımlamak için öğesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="29e58-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="29e58-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29e58-125">See also</span></span>

- [<span data-ttu-id="29e58-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="29e58-126">Configuration file schema for the .NET Framework</span></span>](../index.md)
