---
title: <appSettings> için <add> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 865c693bf8f23bf050064ac097b72aa6fa3b371e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088752"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="a03d4-102">\<appSettings için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="a03d4-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="a03d4-103">Özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="a03d4-103">Adds a custom application setting.</span></span>

<span data-ttu-id="a03d4-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a03d4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a03d4-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="a03d4-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="a03d4-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="a03d4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a03d4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a03d4-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="a03d4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a03d4-108">Attributes</span></span>

|           | <span data-ttu-id="a03d4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a03d4-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a03d4-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="a03d4-110">**key**</span></span>   | <span data-ttu-id="a03d4-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a03d4-111">Required attribute.</span></span><br><br><span data-ttu-id="a03d4-112">Eklenecek anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a03d4-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="a03d4-113">**value**</span><span class="sxs-lookup"><span data-stu-id="a03d4-113">**value**</span></span> | <span data-ttu-id="a03d4-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a03d4-114">Required attribute.</span></span><br><br><span data-ttu-id="a03d4-115">Eklenecek anahtarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a03d4-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a03d4-116">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="a03d4-116">Parent element</span></span>

|     | <span data-ttu-id="a03d4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a03d4-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a03d4-118"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="a03d4-118">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="a03d4-119">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a03d4-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a03d4-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a03d4-120">Child elements</span></span>

<span data-ttu-id="a03d4-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="a03d4-121">None</span></span>

## <a name="example"></a><span data-ttu-id="a03d4-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="a03d4-122">Example</span></span>

<span data-ttu-id="a03d4-123">Aşağıdaki örnek, uygulamanın adı için nasıl özel bir yapılandırma ayarı ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="a03d4-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="a03d4-124">Aşağıdaki örnek, bir ASP.NET uygulamasında iki uyumluluk ayarı tanımlamak için `<add>` öğesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="a03d4-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="a03d4-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a03d4-125">See also</span></span>

- [<span data-ttu-id="a03d4-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="a03d4-126">Configuration file schema for the .NET Framework</span></span>](../index.md)
