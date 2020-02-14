---
title: Uygulama ayarları şeması
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215423"
---
# <a name="app-settings-schema"></a><span data-ttu-id="c4c9f-102">Uygulama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="c4c9f-102">App Settings schema</span></span>

<span data-ttu-id="c4c9f-103">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="c4c9f-104">[ **\<yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4c9f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c4c9f-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="c4c9f-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="c4c9f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add >** ](add-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="c4c9f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)</span></span>\
<span data-ttu-id="c4c9f-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear >** ](clear-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="c4c9f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)</span></span>\
<span data-ttu-id="c4c9f-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Kaldır >** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="c4c9f-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="c4c9f-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4c9f-109">Element</span></span> | <span data-ttu-id="c4c9f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4c9f-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="c4c9f-111"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="c4c9f-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="c4c9f-112">Uygulama ayarlarını denetlemek için **> ekle\<** , **\<Temizle >** ve\<etiketlerini **Kaldır** .</span><span class="sxs-lookup"><span data-stu-id="c4c9f-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="c4c9f-113">, İsteğe bağlı bir **Dosya** özniteliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="c4c9f-114"> **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="c4c9f-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="c4c9f-115">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-115">Defines a setting.</span></span> <span data-ttu-id="c4c9f-116">**\<appSettings >** alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="c4c9f-117">**Anahtar** ve **değer** öznitelikleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="c4c9f-118"> **\<Temizle >** </span><span class="sxs-lookup"><span data-stu-id="c4c9f-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="c4c9f-119">Tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-119">Clears all settings.</span></span> <span data-ttu-id="c4c9f-120">**\<appSettings >** alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="c4c9f-121">Hiç özniteliği yok.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-121">Has no attributes.</span></span> |
| [<span data-ttu-id="c4c9f-122"> **\<> Kaldır**</span><span class="sxs-lookup"><span data-stu-id="c4c9f-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="c4c9f-123">Bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-123">Removes a setting.</span></span> <span data-ttu-id="c4c9f-124">**\<appSettings >** alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="c4c9f-125">**Anahtar** özniteliği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="c4c9f-126">\<appSettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="c4c9f-126">\<appSettings> element</span></span>

<span data-ttu-id="c4c9f-127">Bu öğe, uygulama ayarlarını denetlemek için **> ekle\<** , **\<Temizle >** ve\<etiketlerini **Kaldır** ' ı içerir.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="c4c9f-128">**Dosya**için isteğe bağlı bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="c4c9f-129">\<> öğesi Ekle</span><span class="sxs-lookup"><span data-stu-id="c4c9f-129">\<add> element</span></span>

<span data-ttu-id="c4c9f-130">Uygulama ayarları koleksiyonuna bir ad/değer çifti olarak özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="c4c9f-131">**Anahtar** ve **değer**için öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="c4c9f-132">\<Clear > öğesi</span><span class="sxs-lookup"><span data-stu-id="c4c9f-132">\<clear> element</span></span>

<span data-ttu-id="c4c9f-133">Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve yalnızca **\<clear >** öğesinden sonra > öğeleri **eklemek\<** tarafından eklenen başvuruların kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="c4c9f-134">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="c4c9f-135">\<> öğesi kaldır</span><span class="sxs-lookup"><span data-stu-id="c4c9f-135">\<remove> element</span></span>

<span data-ttu-id="c4c9f-136">Devralınan özel uygulama ayarının başvurusunu uygulama ayarları koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="c4c9f-137">**Anahtar**için bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="c4c9f-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4c9f-138">Example</span></span>

<span data-ttu-id="c4c9f-139">Aşağıdaki örnek, bir özel uygulama ayarı tanımlayan bir dış uygulama ayarları dosyasını (*Custom. config*) gösterir:</span><span class="sxs-lookup"><span data-stu-id="c4c9f-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="c4c9f-140">Aşağıdaki örnek, dış ayarlar dosyasında ayarı tüketen ve kendi uygulama ayarını ayarlayan bir uygulama yapılandırma dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c4c9f-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c4c9f-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4c9f-141">See also</span></span>

- [<span data-ttu-id="c4c9f-142">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c4c9f-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="c4c9f-143">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="c4c9f-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
