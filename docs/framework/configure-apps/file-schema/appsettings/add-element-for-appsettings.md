---
description: 'İçin: öğesi hakkında daha fazla bilgi <add><appSettings>'
title: <appSettings> için <add> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: f10ffe517b3b25543bc7baed0c7d2af13f48ab02
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652893"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="7a2f9-103">\<appSettings> için \<add> öğesi</span><span class="sxs-lookup"><span data-stu-id="7a2f9-103">\<add> element for \<appSettings></span></span>

<span data-ttu-id="7a2f9-104">Özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="7a2f9-104">Adds a custom application setting.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="7a2f9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a2f9-105">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="7a2f9-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7a2f9-106">Attributes</span></span>

|           | <span data-ttu-id="7a2f9-107">Description</span><span class="sxs-lookup"><span data-stu-id="7a2f9-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="7a2f9-108">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="7a2f9-108">**key**</span></span>   | <span data-ttu-id="7a2f9-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7a2f9-109">Required attribute.</span></span><br><br><span data-ttu-id="7a2f9-110">Eklenecek anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a2f9-110">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="7a2f9-111">**değer**</span><span class="sxs-lookup"><span data-stu-id="7a2f9-111">**value**</span></span> | <span data-ttu-id="7a2f9-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7a2f9-112">Required attribute.</span></span><br><br><span data-ttu-id="7a2f9-113">Eklenecek anahtarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a2f9-113">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="7a2f9-114">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="7a2f9-114">Parent element</span></span>

|     | <span data-ttu-id="7a2f9-115">Description</span><span class="sxs-lookup"><span data-stu-id="7a2f9-115">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="7a2f9-116">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7a2f9-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7a2f9-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="7a2f9-117">Child elements</span></span>

<span data-ttu-id="7a2f9-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="7a2f9-118">None</span></span>

## <a name="example"></a><span data-ttu-id="7a2f9-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a2f9-119">Example</span></span>

<span data-ttu-id="7a2f9-120">Aşağıdaki örnek, uygulamanın adı için nasıl özel bir yapılandırma ayarı ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="7a2f9-120">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="7a2f9-121">Aşağıdaki örnek, `<add>` bir ASP.NET uygulamasında iki uyumluluk ayarı tanımlamak için öğesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="7a2f9-121">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="7a2f9-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a2f9-122">See also</span></span>

- [<span data-ttu-id="7a2f9-123">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="7a2f9-123">Configuration file schema for the .NET Framework</span></span>](../index.md)
