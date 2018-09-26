---
title: Uygulama Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f11be59941759687806591feb1edcce28b2119e6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073443"
---
# <a name="application-settings-schema"></a><span data-ttu-id="693e3-102">Uygulama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="693e3-102">Application Settings schema</span></span>

<span data-ttu-id="693e3-103">Uygulama ayarlarını depolamak ve uygulama kapsamlı ve kullanıcı kapsamlı ayarları almak bir Windows Forms veya ASP.NET uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="693e3-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="693e3-104">Bu bağlamda bir *ayarı* herhangi belirli uygulamaya veya geçerli kullanıcının belirli bir bilgi parçasıdır — bir veritabanı bağlantı dizesi kullanıcıya kadar her şeyi varsayılan pencere boyutu tercih edilen.</span><span class="sxs-lookup"><span data-stu-id="693e3-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="693e3-105">Varsayılan olarak, bir Windows Forms uygulamasında uygulama ayarlarını kullanan <xref:System.Configuration.LocalFileSettingsProvider> sınıfını, ki bu ayarları bir XML yapılandırma dosyasında saklamak için .NET yapılandırma sistemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="693e3-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="693e3-106">Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="693e3-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="693e3-107">Uygulama ayarları, kullandığı yapılandırma dosyalarını bir parçası olarak aşağıdaki öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="693e3-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="693e3-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="693e3-108">Element</span></span>                    | <span data-ttu-id="693e3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="693e3-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="693e3-110">**\<applicationSettings >**</span><span class="sxs-lookup"><span data-stu-id="693e3-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="693e3-111">Tüm içeren  **\<ayarı >** etiketler uygulamaya özgü.</span><span class="sxs-lookup"><span data-stu-id="693e3-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="693e3-112">**\<kullanıcı ayarlarını >**</span><span class="sxs-lookup"><span data-stu-id="693e3-112">**\<userSettings>**</span></span>        | <span data-ttu-id="693e3-113">Tüm içeren  **\<ayarı >** geçerli kullanıcıya özel etiketler.</span><span class="sxs-lookup"><span data-stu-id="693e3-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="693e3-114">**\<ayarı >**</span><span class="sxs-lookup"><span data-stu-id="693e3-114">**\<setting>**</span></span>             | <span data-ttu-id="693e3-115">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="693e3-115">Defines a setting.</span></span> <span data-ttu-id="693e3-116">Ya da alt  **\<applicationSettings >** veya  **\<ayarlarını >**.</span><span class="sxs-lookup"><span data-stu-id="693e3-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="693e3-117">**\<Değer >**</span><span class="sxs-lookup"><span data-stu-id="693e3-117">**\<value>**</span></span>               | <span data-ttu-id="693e3-118">Bir ayarın değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="693e3-118">Defines a setting's value.</span></span> <span data-ttu-id="693e3-119">Alt  **\<ayarı >**.</span><span class="sxs-lookup"><span data-stu-id="693e3-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="693e3-120">\<applicationSettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="693e3-120">\<applicationSettings> element</span></span>

<span data-ttu-id="693e3-121">Bu öğe tüm içeren  **\<ayarı >** istemci bilgisayarda uygulamanın bir örneği için özel etiketler.</span><span class="sxs-lookup"><span data-stu-id="693e3-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="693e3-122">Bu öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="693e3-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="693e3-123">\<kullanıcı ayarlarını > öğesi</span><span class="sxs-lookup"><span data-stu-id="693e3-123">\<userSettings> element</span></span>

<span data-ttu-id="693e3-124">Bu öğe tüm içeren  **\<ayarı >** uygulama kullanmakta olduğu kullanıcıya özel etiketler.</span><span class="sxs-lookup"><span data-stu-id="693e3-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="693e3-125">Bu öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="693e3-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="693e3-126">\<ayarı > öğesi</span><span class="sxs-lookup"><span data-stu-id="693e3-126">\<setting> element</span></span>

<span data-ttu-id="693e3-127">Bu öğe bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="693e3-127">This element defines a setting.</span></span> <span data-ttu-id="693e3-128">Bunu, aşağıdaki özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="693e3-128">It has the following attributes.</span></span>

| <span data-ttu-id="693e3-129">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="693e3-129">Attribute</span></span>        | <span data-ttu-id="693e3-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="693e3-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="693e3-131">**Adı**</span><span class="sxs-lookup"><span data-stu-id="693e3-131">**name**</span></span>         | <span data-ttu-id="693e3-132">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="693e3-132">Required.</span></span> <span data-ttu-id="693e3-133">Ayar benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="693e3-133">The unique ID of the setting.</span></span> <span data-ttu-id="693e3-134">Visual Studio aracılığıyla oluşturulan ayarları adı ile kaydedilmiş `ProjectName.Properties.Settings`.</span><span class="sxs-lookup"><span data-stu-id="693e3-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="693e3-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="693e3-135">**serializedAs**</span></span> | <span data-ttu-id="693e3-136">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="693e3-136">Required.</span></span> <span data-ttu-id="693e3-137">Metin değeri serileştirmek için kullanılacak biçimi.</span><span class="sxs-lookup"><span data-stu-id="693e3-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="693e3-138">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="693e3-138">Valid values are:</span></span><br><br><span data-ttu-id="693e3-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="693e3-139">- `string`.</span></span> <span data-ttu-id="693e3-140">Değer bir dize kullanarak olarak serileştirilmiş bir <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="693e3-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="693e3-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="693e3-141">- `xml`.</span></span> <span data-ttu-id="693e3-142">Değer, XML serileştirme kullanarak seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="693e3-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="693e3-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="693e3-143">- `binary`.</span></span> <span data-ttu-id="693e3-144">Değer, ikili serileştirme kullanarak metin ile kodlanmış ikili olarak seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="693e3-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="693e3-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="693e3-145">- `custom`.</span></span> <span data-ttu-id="693e3-146">Ayar sağlayıcısı bu ayar devralmaz sahiptir ve serileştirir ve bunu serileştirir.</span><span class="sxs-lookup"><span data-stu-id="693e3-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="693e3-147">\<Değer > öğesi</span><span class="sxs-lookup"><span data-stu-id="693e3-147">\<value> element</span></span>

<span data-ttu-id="693e3-148">Bu öğe bir ayarın değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="693e3-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="693e3-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="693e3-149">Example</span></span>

<span data-ttu-id="693e3-150">Aşağıdaki örnek iki uygulama kapsamlı ayarlar ve iki kullanıcı kapsamlı ayarları tanımlayan uygulama ayarları dosyası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="693e3-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="693e3-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="693e3-151">See also</span></span>

<span data-ttu-id="693e3-152">[Uygulama ayarlarına genel bakış](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="693e3-152">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="693e3-153">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="693e3-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
