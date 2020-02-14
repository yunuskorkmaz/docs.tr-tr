---
title: <add> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: 5c7de79ec626966e71d461dd3865b294a8979db2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214807"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="9acff-102">\<appSettings için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="9acff-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="9acff-103">Özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="9acff-103">Adds a custom application setting.</span></span>

<span data-ttu-id="9acff-104">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9acff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9acff-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="9acff-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="9acff-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="9acff-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9acff-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9acff-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="9acff-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9acff-108">Attributes</span></span>

|           | <span data-ttu-id="9acff-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9acff-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="9acff-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="9acff-110">**key**</span></span>   | <span data-ttu-id="9acff-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9acff-111">Required attribute.</span></span><br><br><span data-ttu-id="9acff-112">Eklenecek anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9acff-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="9acff-113">**value**</span><span class="sxs-lookup"><span data-stu-id="9acff-113">**value**</span></span> | <span data-ttu-id="9acff-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9acff-114">Required attribute.</span></span><br><br><span data-ttu-id="9acff-115">Eklenecek anahtarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9acff-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="9acff-116">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="9acff-116">Parent element</span></span>

|     | <span data-ttu-id="9acff-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9acff-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9acff-118"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="9acff-118">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="9acff-119">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9acff-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9acff-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="9acff-120">Child elements</span></span>

<span data-ttu-id="9acff-121">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9acff-121">None</span></span>

## <a name="example"></a><span data-ttu-id="9acff-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="9acff-122">Example</span></span>

<span data-ttu-id="9acff-123">Aşağıdaki örnek, uygulamanın adı için nasıl özel bir yapılandırma ayarı ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="9acff-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="9acff-124">Aşağıdaki örnek, bir ASP.NET uygulamasında iki uyumluluk ayarı tanımlamak için `<add>` öğesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="9acff-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="9acff-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9acff-125">See also</span></span>

- [<span data-ttu-id="9acff-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="9acff-126">Configuration file schema for the .NET Framework</span></span>](../index.md)
