---
title: '&lt;appSettings&gt; öğesi için &lt;yapılandırma&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: d17400536b911ce0be4d2bf105b0b4d99d0916df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="cbd5e-102">\<appSettings > öğesi için \<yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="cbd5e-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="cbd5e-103">Özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-103">Contains custom application settings.</span></span> <span data-ttu-id="cbd5e-104">.NET Framework tarafından sağlanan önceden tanımlanmış yapılandırma bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="cbd5e-105">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="cbd5e-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="cbd5e-106">&nbsp;&nbsp;**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="cbd5e-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cbd5e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbd5e-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="cbd5e-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cbd5e-108">Attribute</span></span>

|           | <span data-ttu-id="cbd5e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbd5e-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="cbd5e-110">**Dosya**</span><span class="sxs-lookup"><span data-stu-id="cbd5e-110">**file**</span></span>  | <span data-ttu-id="cbd5e-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-111">Optional attribute.</span></span><br><br><span data-ttu-id="cbd5e-112">Özel uygulama yapılandırma ayarlarını içeren bir dış dosya için göreli bir yol belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="cbd5e-113">Belirtilen dosya aynı tür belirtilen ayarları içerir  **\<Ekle >**,  **\<kaldırma >**, ve  **\<temizleyin >** öğeleri ve aynı anahtar/değer çifti biçimini bu öğeler olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="cbd5e-114">Belirtilen yolu göreli ana yapılandırma dosyası değil.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="cbd5e-115">Bir Windows Forms uygulaması için bu ikili klasördür (örneğin */bin/debug*), uygulama yapılandırma dosyası konumu değil.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="cbd5e-116">Web Forms uygulamaları için uygulama kökü göreli yoludur nerede *web.config* dosyasının bulunduğu.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="cbd5e-117">Belirtilen dosya bulunamadı, çalışma zamanı özniteliği yok sayar unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="cbd5e-118">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="cbd5e-118">Parent element</span></span>

|     | <span data-ttu-id="cbd5e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbd5e-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cbd5e-120">**\<Yapılandırma >** öğesi</span><span class="sxs-lookup"><span data-stu-id="cbd5e-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="cbd5e-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="cbd5e-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="cbd5e-122">Child elements</span></span>

|     | <span data-ttu-id="cbd5e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbd5e-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cbd5e-124">**\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="cbd5e-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="cbd5e-125">Özel uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="cbd5e-126">**\<Clear >**</span><span class="sxs-lookup"><span data-stu-id="cbd5e-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="cbd5e-127">Tüm önceden tanımlanmış uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="cbd5e-128">**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="cbd5e-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="cbd5e-129">Önceden tanımlanmış uygulama ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="cbd5e-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbd5e-130">Remarks</span></span>

<span data-ttu-id="cbd5e-131">**\<AppSettings >** öğesi veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgileri için gibi özel uygulama yapılandırma bilgilerini depolayan bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="cbd5e-132">Belirtilen anahtar/değer çiftlerinin  **\<appSettings >** öğesi kullanılarak kod erişilir <xref:System.Configuration.ConfigurationSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="cbd5e-133">Kullanabileceğiniz **dosya** özniteliğini  **\<appSettings >** öğesinin *Web.config* ve uygulama yapılandırma dosyaları.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="cbd5e-134">Bu öznitelik ek ayarlar sağlayan veya belirtilen ayarları geçersiz kılan bir yapılandırma dosyası belirtir  **\<appSettings >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="cbd5e-135">**Dosya** özniteliği, ne zaman bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak üzere bir kullanıcının istediği gibi kaynak denetim takım geliştirme senaryolarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="cbd5e-136">Yapılandırma dosyaları tarafından belirtilen **dosya** öznitelik, bir kök düğümü olmalıdır  **\<appSettings >** yerine  **\<configuration >**.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="cbd5e-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="cbd5e-137">Example</span></span>

<span data-ttu-id="cbd5e-138">Aşağıdaki örnek, bir dış uygulama ayarları dosyası gösterir (*custom.config*), özel uygulama ayarını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="cbd5e-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="cbd5e-139">Aşağıdaki örnek, dış ayarları dosyasında ayarı kullanır ve bir uygulama ayarı kendi ayarlar uygulama yapılandırma dosyası gösterir:</span><span class="sxs-lookup"><span data-stu-id="cbd5e-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="cbd5e-140">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="cbd5e-140">Configuration file</span></span>

<span data-ttu-id="cbd5e-141">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbd5e-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbd5e-142">See also</span></span>

[<span data-ttu-id="cbd5e-143">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="cbd5e-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
