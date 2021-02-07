---
description: 'Daha fazla bilgi edinin: uygulama ayarları şeması'
title: Uygulama ayarları şeması
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: a98a60b0470e0fa2c03313f25de9b310f5fce785
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699356"
---
# <a name="app-settings-schema"></a><span data-ttu-id="6984c-103">Uygulama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6984c-103">App Settings schema</span></span>

<span data-ttu-id="6984c-104">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6984c-104">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="6984c-105">Öğe</span><span class="sxs-lookup"><span data-stu-id="6984c-105">Element</span></span> | <span data-ttu-id="6984c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6984c-106">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="6984c-107">**\<add>** **\<clear>** **\<remove>** Uygulama ayarlarını denetlemek için, ve etiketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6984c-107">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="6984c-108">, İsteğe bağlı bir **Dosya** özniteliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6984c-108">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="6984c-109">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6984c-109">Defines a setting.</span></span> <span data-ttu-id="6984c-110">Alt öğesi **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="6984c-110">Child of **\<appSettings>**.</span></span> <span data-ttu-id="6984c-111">**Anahtar** ve **değer** öznitelikleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6984c-111">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="6984c-112">Tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="6984c-112">Clears all settings.</span></span> <span data-ttu-id="6984c-113">Alt öğesi **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="6984c-113">Child of **\<appSettings>**.</span></span> <span data-ttu-id="6984c-114">Hiç özniteliği yok.</span><span class="sxs-lookup"><span data-stu-id="6984c-114">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="6984c-115">Bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6984c-115">Removes a setting.</span></span> <span data-ttu-id="6984c-116">Alt öğesi **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="6984c-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="6984c-117">**Anahtar** özniteliği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6984c-117">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="6984c-118">\<appSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="6984c-118">\<appSettings> element</span></span>

<span data-ttu-id="6984c-119">Bu öğe, **\<add>** **\<clear>** **\<remove>** uygulama ayarlarını denetlemek için, ve etiketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6984c-119">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="6984c-120">**Dosya** için isteğe bağlı bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6984c-120">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="6984c-121">\<add> öğesi</span><span class="sxs-lookup"><span data-stu-id="6984c-121">\<add> element</span></span>

<span data-ttu-id="6984c-122">Uygulama ayarları koleksiyonuna bir ad/değer çifti olarak özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="6984c-122">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="6984c-123">**Anahtar** ve **değer** için öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6984c-123">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="6984c-124">\<clear> öğesi</span><span class="sxs-lookup"><span data-stu-id="6984c-124">\<clear> element</span></span>

<span data-ttu-id="6984c-125">Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve yalnızca öğesini izleyen öğeler tarafından eklenen başvurulara izin verir **\<add>** **\<clear>** .</span><span class="sxs-lookup"><span data-stu-id="6984c-125">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="6984c-126">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="6984c-126">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="6984c-127">\<remove> öğesi</span><span class="sxs-lookup"><span data-stu-id="6984c-127">\<remove> element</span></span>

<span data-ttu-id="6984c-128">Devralınan özel uygulama ayarının başvurusunu uygulama ayarları koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6984c-128">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="6984c-129">**Anahtar** için bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6984c-129">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="6984c-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="6984c-130">Example</span></span>

<span data-ttu-id="6984c-131">Aşağıdaki örnek, bir özel uygulama ayarı tanımlayan bir dış uygulama ayarları dosyası (*custom.config*) göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="6984c-131">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="6984c-132">Aşağıdaki örnek, dış ayarlar dosyasında ayarı tüketen ve kendi uygulama ayarını ayarlayan bir uygulama yapılandırma dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6984c-132">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6984c-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6984c-133">See also</span></span>

- [<span data-ttu-id="6984c-134">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6984c-134">Application Settings Overview</span></span>](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [<span data-ttu-id="6984c-135">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="6984c-135">Application Settings Architecture</span></span>](/dotnet/desktop/winforms/advanced/application-settings-architecture)
