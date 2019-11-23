---
title: <appSettings> için <configuration> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6112d87afcca8b2f54508d03d3ea4c0781d7e475
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119277"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="c42b4-102">\<yapılandırması için \<appSettings > öğesi ></span><span class="sxs-lookup"><span data-stu-id="c42b4-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="c42b4-103">Özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-103">Contains custom application settings.</span></span> <span data-ttu-id="c42b4-104">Bu, .NET Framework tarafından sunulan önceden tanımlanmış bir yapılandırma bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="c42b4-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="c42b4-105">[ **\<yapılandırma >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c42b4-105">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="c42b4-106">&nbsp;&nbsp; **\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="c42b4-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c42b4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c42b4-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="c42b4-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c42b4-108">Attribute</span></span>

|           | <span data-ttu-id="c42b4-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c42b4-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c42b4-110">**dosyasýný**</span><span class="sxs-lookup"><span data-stu-id="c42b4-110">**file**</span></span>  | <span data-ttu-id="c42b4-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c42b4-111">Optional attribute.</span></span><br><br><span data-ttu-id="c42b4-112">Özel uygulama yapılandırma ayarlarını içeren bir dış dosyanın göreli yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="c42b4-113">Belirtilen dosya **\<> eklemek**, **> kaldırmak\<** ve\<**Temizle >** öğelerini ve bu öğelerle aynı anahtar/değer çifti biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c42b4-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="c42b4-114">Belirtilen yol, ana yapılandırma dosyasına göredir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="c42b4-115">Windows Forms bir uygulama için, bu, uygulama yapılandırma dosyasının konumunu değil, ikili klasördür (örneğin, */bin/Debug*).</span><span class="sxs-lookup"><span data-stu-id="c42b4-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="c42b4-116">Web Forms uygulamalar için yol, *Web. config* dosyasının bulunduğu uygulama köküne göredir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="c42b4-117">Belirtilen dosya bulunamazsa çalışma zamanının özniteliği yoksaydığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c42b4-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c42b4-118">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="c42b4-118">Parent element</span></span>

|     | <span data-ttu-id="c42b4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c42b4-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c42b4-120"> **\<yapılandırma >** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="c42b4-120">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="c42b4-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c42b4-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c42b4-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c42b4-122">Child elements</span></span>

|     | <span data-ttu-id="c42b4-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c42b4-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c42b4-124"> **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="c42b4-124">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="c42b4-125">Özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="c42b4-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="c42b4-126"> **\<Temizle >** </span><span class="sxs-lookup"><span data-stu-id="c42b4-126">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="c42b4-127">Önceden tanımlanmış tüm uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="c42b4-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="c42b4-128"> **\<> Kaldır**</span><span class="sxs-lookup"><span data-stu-id="c42b4-128">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="c42b4-129">Önceden tanımlanmış bir uygulama ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c42b4-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c42b4-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c42b4-130">Remarks</span></span>

<span data-ttu-id="c42b4-131">**\<AppSettings >** öğesi veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgileri için gibi özel bir uygulama yapılandırma bilgilerini depolayan bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="c42b4-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="c42b4-132">**\<appSettings >** öğesinde belirtilen anahtar/değer çiftlerine <xref:System.Configuration.ConfigurationSettings> sınıfı kullanılarak kodla erişilir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="c42b4-133">*Web. config* ve uygulama yapılandırma dosyalarının **\<appSettings >** öğesinde **Dosya** özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c42b4-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="c42b4-134">Bu öznitelik, ek ayarlar sağlayan veya **\<appSettings >** öğesinde belirtilen ayarları geçersiz kılan bir yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="c42b4-135">**Dosya** özniteliği, bir Kullanıcı bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak istediğinde olduğu gibi, kaynak denetimi takım geliştirme senaryolarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="c42b4-136">Yapılandırma dosyaları tarafından belirtilen **dosya** öznitelik, bir kök düğümü olmalıdır **\<appSettings >** yerine **\<yapılandırma >** .</span><span class="sxs-lookup"><span data-stu-id="c42b4-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="c42b4-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="c42b4-137">Example</span></span>

<span data-ttu-id="c42b4-138">Aşağıdaki örnek, bir özel uygulama ayarı tanımlayan bir dış uygulama ayarları dosyasını (*Custom. config*) gösterir:</span><span class="sxs-lookup"><span data-stu-id="c42b4-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="c42b4-139">Aşağıdaki örnek, dış ayarlar dosyasında ayarı tüketen ve kendi uygulama ayarını ayarlayan bir uygulama yapılandırma dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c42b4-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c42b4-140">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="c42b4-140">Configuration file</span></span>

<span data-ttu-id="c42b4-141">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c42b4-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c42b4-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c42b4-142">See also</span></span>

- [<span data-ttu-id="c42b4-143">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="c42b4-143">Configuration file schema for the .NET Framework</span></span>](../index.md)
