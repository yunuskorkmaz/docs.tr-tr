---
title: Uygulama Ayarları Şeması
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 548d93e5447c06480629658b13b673aa3d15fc86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705473"
---
# <a name="app-settings-schema"></a><span data-ttu-id="962b7-102">Uygulama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="962b7-102">App Settings schema</span></span>

<span data-ttu-id="962b7-103">Dosya yolları, XML Web hizmeti URL'leri ya da bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="962b7-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="962b7-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="962b7-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="962b7-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="962b7-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="962b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="962b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="962b7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<Temizleme >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="962b7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="962b7-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="962b7-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="962b7-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="962b7-109">Element</span></span> | <span data-ttu-id="962b7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="962b7-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="962b7-111">**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="962b7-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="962b7-112">İçeren  **\<Ekle >**,  **\<Temizle >**, ve  **\<kaldırma >** denetimi uygulama ayarlarına etiketler.</span><span class="sxs-lookup"><span data-stu-id="962b7-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="962b7-113">İsteğe bağlı olan **dosya** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="962b7-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="962b7-114">**\<Ekle >**</span><span class="sxs-lookup"><span data-stu-id="962b7-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="962b7-115">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="962b7-115">Defines a setting.</span></span> <span data-ttu-id="962b7-116">Alt  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="962b7-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="962b7-117">Gerektirir **anahtarı** ve **değer** öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="962b7-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="962b7-118">**\<Temizleme >**</span><span class="sxs-lookup"><span data-stu-id="962b7-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="962b7-119">Tüm ayarları siler.</span><span class="sxs-lookup"><span data-stu-id="962b7-119">Clears all settings.</span></span> <span data-ttu-id="962b7-120">Alt  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="962b7-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="962b7-121">öznitelikleri yok.</span><span class="sxs-lookup"><span data-stu-id="962b7-121">Has no attributes.</span></span> |
| [<span data-ttu-id="962b7-122">**\<kaldırma >**</span><span class="sxs-lookup"><span data-stu-id="962b7-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="962b7-123">Bir ayar kaldırır.</span><span class="sxs-lookup"><span data-stu-id="962b7-123">Removes a setting.</span></span> <span data-ttu-id="962b7-124">Alt  **\<appSettings >**.</span><span class="sxs-lookup"><span data-stu-id="962b7-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="962b7-125">Gerektiren bir **anahtar** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="962b7-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="962b7-126">\<appSettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="962b7-126">\<appSettings> element</span></span>

<span data-ttu-id="962b7-127">Bu öğeyi içeren  **\<Ekle >**,  **\<Temizle >**, ve  **\<kaldırma >** denetimi uygulama ayarlarına etiketler.</span><span class="sxs-lookup"><span data-stu-id="962b7-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="962b7-128">İçin isteğe bağlı bir öznitelik tanımlar **dosya**.</span><span class="sxs-lookup"><span data-stu-id="962b7-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="962b7-129">\<Ekle > öğesi</span><span class="sxs-lookup"><span data-stu-id="962b7-129">\<add> element</span></span>

<span data-ttu-id="962b7-130">Özel uygulama ayarı adı/değer çifti olarak uygulama ayarlarını koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="962b7-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="962b7-131">İçin öznitelikleri tanımlar **anahtarı** ve **değer**.</span><span class="sxs-lookup"><span data-stu-id="962b7-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="962b7-132">\<Temizle > öğesi</span><span class="sxs-lookup"><span data-stu-id="962b7-132">\<clear> element</span></span>

<span data-ttu-id="962b7-133">Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve tarafından eklenen başvuruları sağlayan  **\<Ekle >** aşağıdaki öğeleri  **\<Temizle >** öğe.</span><span class="sxs-lookup"><span data-stu-id="962b7-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="962b7-134">Bu öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="962b7-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="962b7-135">\<kaldırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="962b7-135">\<remove> element</span></span>

<span data-ttu-id="962b7-136">Devralınan özel uygulama ayarı için bir başvuru uygulaması ayarları koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="962b7-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="962b7-137">İçin bir öznitelik tanımlar **anahtar**.</span><span class="sxs-lookup"><span data-stu-id="962b7-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="962b7-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="962b7-138">Example</span></span>

<span data-ttu-id="962b7-139">Aşağıdaki örnek, bir dış uygulama ayarları dosyasından gösterir (*custom.config*), özel uygulama ayarını tanımlar:</span><span class="sxs-lookup"><span data-stu-id="962b7-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="962b7-140">Aşağıdaki örnek, dış ayarları dosyası ayarı kullanır ve bir uygulama ayarı kendi ayarlar uygulama yapılandırma dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="962b7-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="962b7-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="962b7-141">See also</span></span>

- [<span data-ttu-id="962b7-142">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="962b7-142">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="962b7-143">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="962b7-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
