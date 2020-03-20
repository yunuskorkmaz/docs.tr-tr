---
title: <configuration> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155537"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="78489-102">\<yapılandırma> için \<> öğesi</span><span class="sxs-lookup"><span data-stu-id="78489-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="78489-103">Özel uygulama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="78489-103">Contains custom application settings.</span></span> <span data-ttu-id="78489-104">Bu, .NET Framework tarafından sağlanan önceden tanımlanmış bir yapılandırma bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="78489-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="78489-105">yapılandırma &nbsp; &nbsp;>[\*\* \<\*\*](../configuration-element.md) \*\* \<appAyarlar>\*\*</span><span class="sxs-lookup"><span data-stu-id="78489-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="78489-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78489-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="78489-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="78489-107">Attribute</span></span>

|           | <span data-ttu-id="78489-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78489-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="78489-109">**Dosya**</span><span class="sxs-lookup"><span data-stu-id="78489-109">**file**</span></span>  | <span data-ttu-id="78489-110">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="78489-110">Optional attribute.</span></span><br><br><span data-ttu-id="78489-111">Özel uygulama yapılandırma ayarları içeren harici bir dosyaya göreli bir yol belirtir.</span><span class="sxs-lookup"><span data-stu-id="78489-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="78489-112">Belirtilen dosya, \*\* \<>ekleme, \*\* \*\* \<>kaldırma **ve \*\* \<>öğelerini temizleme** de belirtilen ayarların aynı türünü içerir ve bu öğelerle aynı anahtar/değer çifti biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="78489-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="78489-113">Belirtilen yol ana yapılandırma dosyasına göredir.</span><span class="sxs-lookup"><span data-stu-id="78489-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="78489-114">Windows Forms uygulaması için bu ikili klasördür *(//bin/hata ayıklama*gibi), uygulama yapılandırma dosyasının konumu değildir.</span><span class="sxs-lookup"><span data-stu-id="78489-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="78489-115">Web Formları uygulamaları için yol, *web.config* dosyasının bulunduğu uygulama köküne göredir.</span><span class="sxs-lookup"><span data-stu-id="78489-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="78489-116">Belirtilen dosya bulunamazsa çalışma süresi özniteliği yok sayar.</span><span class="sxs-lookup"><span data-stu-id="78489-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="78489-117">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="78489-117">Parent element</span></span>

|     | <span data-ttu-id="78489-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78489-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="78489-119">\*\* \<yapılandırma>\*\* Öğe</span><span class="sxs-lookup"><span data-stu-id="78489-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="78489-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="78489-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="78489-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="78489-121">Child elements</span></span>

|     | <span data-ttu-id="78489-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78489-122">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="78489-123">**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="78489-123">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="78489-124">Özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="78489-124">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="78489-125">**\<açık>**</span><span class="sxs-lookup"><span data-stu-id="78489-125">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="78489-126">Daha önce tanımlanmış tüm uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="78489-126">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="78489-127">**\<>kaldırmak**</span><span class="sxs-lookup"><span data-stu-id="78489-127">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="78489-128">Daha önce tanımlanmış bir uygulama ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="78489-128">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="78489-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78489-129">Remarks</span></span>

<span data-ttu-id="78489-130">AppSettings>öğesi veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL'leri veya bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama yapılandırma bilgilerini depolar. \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="78489-130">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="78489-131">\*\* \<Uygulama Ayarları>\*\* öğesinde belirtilen anahtar/değer çiftleri <xref:System.Configuration.ConfigurationSettings> sınıf kullanılarak kod olarak erişilir.</span><span class="sxs-lookup"><span data-stu-id="78489-131">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="78489-132">*Web.config* ve uygulama yapılandırma dosyalarının \*\* \<appSettings>\*\* öğesinde **dosya** özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78489-132">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="78489-133">Bu öznitelik, ek ayarlar sağlayan veya \*\* \<uygulama Ayarları>\*\* öğesinde belirtilen ayarları geçersiz kılan bir yapılandırma dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="78489-133">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="78489-134">**Dosya** özniteliği, kullanıcının bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak istemesi gibi kaynak denetimi ekibi geliştirme senaryolarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78489-134">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="78489-135">**Dosya** özniteliği tarafından belirtilen yapılandırma dosyaları, \*\* \<yapılandırma>\*\* yerine \*\* \<>appSettings\*\* kök düğümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78489-135">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="78489-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="78489-136">Example</span></span>

<span data-ttu-id="78489-137">Aşağıdaki örnek, özel bir uygulama ayarı tanımlayan harici bir uygulama ayarları dosyasını *(custom.config)* gösterir:</span><span class="sxs-lookup"><span data-stu-id="78489-137">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="78489-138">Aşağıdaki örnek, dış ayarlar dosyasındaki ayarı tüketen ve kendi uygulama ayarını ayarlayan bir uygulama yapılandırma dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="78489-138">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="78489-139">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="78489-139">Configuration file</span></span>

<span data-ttu-id="78489-140">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78489-140">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="78489-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78489-141">See also</span></span>

- [<span data-ttu-id="78489-142">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="78489-142">Configuration file schema for the .NET Framework</span></span>](../index.md)
