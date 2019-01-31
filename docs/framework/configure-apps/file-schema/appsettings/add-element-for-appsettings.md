---
title: <add> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dde773dc722cf75da9d922ccf28af4bf4a09636c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277478"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="2416b-102">\<Ekle > öğesi için \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="2416b-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="2416b-103">Özel uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="2416b-103">Adds a custom application setting.</span></span>

<span data-ttu-id="2416b-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2416b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="2416b-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="2416b-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="2416b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span><span class="sxs-lookup"><span data-stu-id="2416b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2416b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2416b-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="2416b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2416b-108">Attributes</span></span>

|           | <span data-ttu-id="2416b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2416b-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="2416b-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="2416b-110">**key**</span></span>   | <span data-ttu-id="2416b-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2416b-111">Required attribute.</span></span><br><br><span data-ttu-id="2416b-112">Eklenecek anahtar adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2416b-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="2416b-113">**value**</span><span class="sxs-lookup"><span data-stu-id="2416b-113">**value**</span></span> | <span data-ttu-id="2416b-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2416b-114">Required attribute.</span></span><br><br><span data-ttu-id="2416b-115">Eklenecek anahtar değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2416b-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="2416b-116">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="2416b-116">Parent element</span></span>

|     | <span data-ttu-id="2416b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2416b-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2416b-118">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="2416b-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="2416b-119">Dosya yolları, XML Web hizmeti URL'leri ya da bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="2416b-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2416b-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2416b-120">Child elements</span></span>

<span data-ttu-id="2416b-121">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="2416b-121">None</span></span>

## <a name="example"></a><span data-ttu-id="2416b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="2416b-122">Example</span></span>

<span data-ttu-id="2416b-123">Aşağıdaki örnek, bir uygulamanın adı için özel yapılandırma ayarı eklemek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2416b-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="2416b-124">Aşağıdaki örnekte `<add>` bir ASP.NET uygulamasında iki uyumluluk ayarlarını tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="2416b-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="2416b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2416b-125">See also</span></span>

- [<span data-ttu-id="2416b-126">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="2416b-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
