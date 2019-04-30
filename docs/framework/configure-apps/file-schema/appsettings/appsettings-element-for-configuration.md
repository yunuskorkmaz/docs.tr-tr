---
title: <configuration> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dcdf8d0f11ae65353da08bba1f8d2fe5ab415c6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705564"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="ff17f-102">\<appSettings > öğesi için \<yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="ff17f-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="ff17f-103">Özel uygulama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ff17f-103">Contains custom application settings.</span></span> <span data-ttu-id="ff17f-104">.NET Framework tarafından sağlanan önceden tanımlanmış yapılandırma bölümü budur.</span><span class="sxs-lookup"><span data-stu-id="ff17f-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="ff17f-105">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ff17f-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="ff17f-106">&nbsp;&nbsp;**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="ff17f-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ff17f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff17f-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="ff17f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ff17f-108">Attribute</span></span>

|           | <span data-ttu-id="ff17f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff17f-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="ff17f-110">**Dosya**</span><span class="sxs-lookup"><span data-stu-id="ff17f-110">**file**</span></span>  | <span data-ttu-id="ff17f-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ff17f-111">Optional attribute.</span></span><br><br><span data-ttu-id="ff17f-112">Özel uygulama yapılandırma ayarlarını içeren bir dış dosya için göreli bir yol belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff17f-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="ff17f-113">Belirtilen dosya aynı tür içinde belirtilen ayarları içeren  **\<Ekle >**,  **\<kaldırma >**, ve  **\<Temizle >** öğeleri ve kullanıyor aynı anahtar/değer çifti bu öğeler biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="ff17f-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="ff17f-114">Belirtilen yol göreli ana yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ff17f-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="ff17f-115">Bir Windows Forms uygulaması için bu ikili klasördür (örneğin */bin/debug*), uygulama yapılandırma dosyası konumu değil.</span><span class="sxs-lookup"><span data-stu-id="ff17f-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="ff17f-116">Web Forms uygulamaları için uygulama köküne göreli yoludur burada *web.config* dosyasının bulunduğu.</span><span class="sxs-lookup"><span data-stu-id="ff17f-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="ff17f-117">Belirtilen dosya bulunamadı, çalışma zamanı öznitelik yoksaydığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ff17f-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="ff17f-118">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="ff17f-118">Parent element</span></span>

|     | <span data-ttu-id="ff17f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff17f-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ff17f-120">**\<Yapılandırma >** öğesi</span><span class="sxs-lookup"><span data-stu-id="ff17f-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="ff17f-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ff17f-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ff17f-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ff17f-122">Child elements</span></span>

|     | <span data-ttu-id="ff17f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff17f-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ff17f-124">**\<Ekle >**</span><span class="sxs-lookup"><span data-stu-id="ff17f-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="ff17f-125">Özel uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="ff17f-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="ff17f-126">**\<Temizleme >**</span><span class="sxs-lookup"><span data-stu-id="ff17f-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="ff17f-127">Tüm önceden tanımlanmış uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="ff17f-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="ff17f-128">**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="ff17f-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="ff17f-129">Önceden tanımlanmış uygulama ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ff17f-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ff17f-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff17f-130">Remarks</span></span>

<span data-ttu-id="ff17f-131">**\<AppSettings >** öğesi veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgileri için gibi özel bir uygulama yapılandırma bilgilerini depolayan bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="ff17f-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="ff17f-132">Belirtilen anahtar/değer çiftleri  **\<appSettings >** öğesi kullanılarak koddan erişilebilir <xref:System.Configuration.ConfigurationSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ff17f-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="ff17f-133">Kullanabileceğiniz **dosya** özniteliğini  **\<appSettings >** öğesinin *Web.config* ve uygulama yapılandırma dosyaları.</span><span class="sxs-lookup"><span data-stu-id="ff17f-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="ff17f-134">Bu öznitelik belirtilen ayarları geçersiz kılar veya ek ayarlar sağlayan bir yapılandırma dosyası belirtir  **\<appSettings >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="ff17f-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="ff17f-135">**Dosya** özniteliği, ne zaman bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak bir kullanıcının istediği gibi kaynak denetimi takım geliştirme senaryolarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff17f-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="ff17f-136">Yapılandırma dosyaları tarafından belirtilen **dosya** öznitelik, bir kök düğümü olmalıdır **\<appSettings >** yerine **\<yapılandırma >**.</span><span class="sxs-lookup"><span data-stu-id="ff17f-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="ff17f-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff17f-137">Example</span></span>

<span data-ttu-id="ff17f-138">Aşağıdaki örnek, bir dış uygulama ayarları dosyasından gösterir (*custom.config*), özel uygulama ayarını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="ff17f-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="ff17f-139">Aşağıdaki örnek, dış ayarları dosyası ayarı kullanır ve bir uygulama ayarı kendi ayarlar uygulama yapılandırma dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ff17f-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="ff17f-140">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="ff17f-140">Configuration file</span></span>

<span data-ttu-id="ff17f-141">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="ff17f-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff17f-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff17f-142">See also</span></span>

- [<span data-ttu-id="ff17f-143">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ff17f-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
