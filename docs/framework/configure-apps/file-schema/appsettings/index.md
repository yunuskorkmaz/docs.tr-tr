---
title: Uygulama ayarları şeması
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 609ddba9cd4d58f9c388cf669039ee128e87efd0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088074"
---
# <a name="app-settings-schema"></a><span data-ttu-id="fed96-102">Uygulama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="fed96-102">App Settings schema</span></span>

<span data-ttu-id="fed96-103">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="fed96-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="fed96-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="fed96-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fed96-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="fed96-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="fed96-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add >** ](add-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="fed96-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)</span></span>\
<span data-ttu-id="fed96-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear >** ](clear-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="fed96-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)</span></span>\
<span data-ttu-id="fed96-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Kaldır >** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="fed96-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="fed96-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="fed96-109">Element</span></span> | <span data-ttu-id="fed96-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fed96-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="fed96-111"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="fed96-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="fed96-112">Uygulama ayarlarını denetlemek için **> ekle\<** , **\<Temizle >** ve\<etiketlerini **Kaldır** .</span><span class="sxs-lookup"><span data-stu-id="fed96-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="fed96-113">, İsteğe bağlı bir **Dosya** özniteliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fed96-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="fed96-114"> **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="fed96-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="fed96-115">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fed96-115">Defines a setting.</span></span> <span data-ttu-id="fed96-116">**\<appSettings >** alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="fed96-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="fed96-117">**Anahtar** ve **değer** öznitelikleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fed96-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="fed96-118"> **\<Temizle >** </span><span class="sxs-lookup"><span data-stu-id="fed96-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="fed96-119">Tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="fed96-119">Clears all settings.</span></span> <span data-ttu-id="fed96-120">**\<appSettings >** alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="fed96-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="fed96-121">Hiç özniteliği yok.</span><span class="sxs-lookup"><span data-stu-id="fed96-121">Has no attributes.</span></span> |
| [<span data-ttu-id="fed96-122"> **\<> Kaldır**</span><span class="sxs-lookup"><span data-stu-id="fed96-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="fed96-123">Bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fed96-123">Removes a setting.</span></span> <span data-ttu-id="fed96-124">**\<appSettings >** alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="fed96-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="fed96-125">**Anahtar** özniteliği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fed96-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="fed96-126">\<appSettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="fed96-126">\<appSettings> element</span></span>

<span data-ttu-id="fed96-127">Bu öğe, uygulama ayarlarını denetlemek için **> ekle\<** , **\<Temizle >** ve\<etiketlerini **Kaldır** ' ı içerir.</span><span class="sxs-lookup"><span data-stu-id="fed96-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="fed96-128">**Dosya**için isteğe bağlı bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fed96-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="fed96-129">\<> öğesi Ekle</span><span class="sxs-lookup"><span data-stu-id="fed96-129">\<add> element</span></span>

<span data-ttu-id="fed96-130">Uygulama ayarları koleksiyonuna bir ad/değer çifti olarak özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="fed96-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="fed96-131">**Anahtar** ve **değer**için öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fed96-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="fed96-132">\<Clear > öğesi</span><span class="sxs-lookup"><span data-stu-id="fed96-132">\<clear> element</span></span>

<span data-ttu-id="fed96-133">Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve yalnızca **\<clear >** öğesinden sonra > öğeleri **eklemek\<** tarafından eklenen başvuruların kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="fed96-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="fed96-134">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="fed96-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="fed96-135">\<> öğesi kaldır</span><span class="sxs-lookup"><span data-stu-id="fed96-135">\<remove> element</span></span>

<span data-ttu-id="fed96-136">Devralınan özel uygulama ayarının başvurusunu uygulama ayarları koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fed96-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="fed96-137">**Anahtar**için bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fed96-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="fed96-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="fed96-138">Example</span></span>

<span data-ttu-id="fed96-139">Aşağıdaki örnek, bir özel uygulama ayarı tanımlayan bir dış uygulama ayarları dosyasını (*Custom. config*) gösterir:</span><span class="sxs-lookup"><span data-stu-id="fed96-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="fed96-140">Aşağıdaki örnek, dış ayarlar dosyasında ayarı tüketen ve kendi uygulama ayarını ayarlayan bir uygulama yapılandırma dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="fed96-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="fed96-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fed96-141">See also</span></span>

- [<span data-ttu-id="fed96-142">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fed96-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="fed96-143">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="fed96-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
