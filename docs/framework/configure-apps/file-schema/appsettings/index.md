---
title: Uygulama ayarları şeması
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: a67689bd9757f7586881fd910ef6103b1dffeab8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550455"
---
# <a name="app-settings-schema"></a><span data-ttu-id="f8698-102">Uygulama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="f8698-102">App Settings schema</span></span>

<span data-ttu-id="f8698-103">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f8698-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="f8698-104">Öğe</span><span class="sxs-lookup"><span data-stu-id="f8698-104">Element</span></span> | <span data-ttu-id="f8698-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8698-105">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="f8698-106">**\<add>** **\<clear>** **\<remove>** Uygulama ayarlarını denetlemek için, ve etiketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f8698-106">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f8698-107">, İsteğe bağlı bir **Dosya** özniteliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f8698-107">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="f8698-108">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8698-108">Defines a setting.</span></span> <span data-ttu-id="f8698-109">Alt öğesi **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="f8698-109">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f8698-110">**Anahtar** ve **değer** öznitelikleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8698-110">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="f8698-111">Tüm ayarları temizler.</span><span class="sxs-lookup"><span data-stu-id="f8698-111">Clears all settings.</span></span> <span data-ttu-id="f8698-112">Alt öğesi **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="f8698-112">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f8698-113">Hiç özniteliği yok.</span><span class="sxs-lookup"><span data-stu-id="f8698-113">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="f8698-114">Bir ayarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f8698-114">Removes a setting.</span></span> <span data-ttu-id="f8698-115">Alt öğesi **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="f8698-115">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f8698-116">**Anahtar** özniteliği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8698-116">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="f8698-117">\<appSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="f8698-117">\<appSettings> element</span></span>

<span data-ttu-id="f8698-118">Bu öğe, **\<add>** **\<clear>** **\<remove>** uygulama ayarlarını denetlemek için, ve etiketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f8698-118">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f8698-119">**Dosya**için isteğe bağlı bir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8698-119">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="f8698-120">\<add> öğesi</span><span class="sxs-lookup"><span data-stu-id="f8698-120">\<add> element</span></span>

<span data-ttu-id="f8698-121">Uygulama ayarları koleksiyonuna bir ad/değer çifti olarak özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="f8698-121">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="f8698-122">**Anahtar** ve **değer**için öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8698-122">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="f8698-123">\<clear> öğesi</span><span class="sxs-lookup"><span data-stu-id="f8698-123">\<clear> element</span></span>

<span data-ttu-id="f8698-124">Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve yalnızca öğesini izleyen öğeler tarafından eklenen başvurulara izin verir **\<add>** **\<clear>** .</span><span class="sxs-lookup"><span data-stu-id="f8698-124">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="f8698-125">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="f8698-125">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="f8698-126">\<remove> öğesi</span><span class="sxs-lookup"><span data-stu-id="f8698-126">\<remove> element</span></span>

<span data-ttu-id="f8698-127">Devralınan özel uygulama ayarının başvurusunu uygulama ayarları koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f8698-127">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="f8698-128">**Anahtar**için bir özniteliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8698-128">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="f8698-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8698-129">Example</span></span>

<span data-ttu-id="f8698-130">Aşağıdaki örnek, bir özel uygulama ayarı tanımlayan bir dış uygulama ayarları dosyası (*custom.config*) göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f8698-130">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="f8698-131">Aşağıdaki örnek, dış ayarlar dosyasında ayarı tüketen ve kendi uygulama ayarını ayarlayan bir uygulama yapılandırma dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f8698-131">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f8698-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8698-132">See also</span></span>

- [<span data-ttu-id="f8698-133">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f8698-133">Application Settings Overview</span></span>](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [<span data-ttu-id="f8698-134">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="f8698-134">Application Settings Architecture</span></span>](/dotnet/desktop/winforms/advanced/application-settings-architecture)
