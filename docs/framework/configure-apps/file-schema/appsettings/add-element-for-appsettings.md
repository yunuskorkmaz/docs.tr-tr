---
title: <appSettings> için <add> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: 5c7de79ec626966e71d461dd3865b294a8979db2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214807"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="35048-102">\<appSettings> için \<add> öğesi</span><span class="sxs-lookup"><span data-stu-id="35048-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="35048-103">Özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="35048-103">Adds a custom application setting.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="35048-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35048-104">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="35048-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="35048-105">Attributes</span></span>

|           | <span data-ttu-id="35048-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35048-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="35048-107">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="35048-107">**key**</span></span>   | <span data-ttu-id="35048-108">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="35048-108">Required attribute.</span></span><br><br><span data-ttu-id="35048-109">Eklenecek anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35048-109">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="35048-110">**deeri**</span><span class="sxs-lookup"><span data-stu-id="35048-110">**value**</span></span> | <span data-ttu-id="35048-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="35048-111">Required attribute.</span></span><br><br><span data-ttu-id="35048-112">Eklenecek anahtarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="35048-112">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="35048-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="35048-113">Parent element</span></span>

|     | <span data-ttu-id="35048-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35048-114">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="35048-115">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="35048-115">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="35048-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="35048-116">Child elements</span></span>

<span data-ttu-id="35048-117">Yok</span><span class="sxs-lookup"><span data-stu-id="35048-117">None</span></span>

## <a name="example"></a><span data-ttu-id="35048-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="35048-118">Example</span></span>

<span data-ttu-id="35048-119">Aşağıdaki örnek, uygulamanın adı için nasıl özel bir yapılandırma ayarı ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="35048-119">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="35048-120">Aşağıdaki örnek, `<add>` bir ASP.NET uygulamasında iki uyumluluk ayarı tanımlamak için öğesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="35048-120">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="35048-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35048-121">See also</span></span>

- [<span data-ttu-id="35048-122">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="35048-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
