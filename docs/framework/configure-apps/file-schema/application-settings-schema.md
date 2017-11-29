---
title: "Uygulama Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
caps.latest.revision: "3"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d93a18b17e0d6b8e413903fb84dc6b427d94f6af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="application-settings-schema"></a><span data-ttu-id="526ab-102">Uygulama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="526ab-102">Application Settings schema</span></span>

<span data-ttu-id="526ab-103">Uygulama ayarlarını depolamak ve uygulama kapsamlı ve kullanıcı kapsamlı ayarlarını almak bir Windows Forms ya da ASP.NET uygulamasının izin verin.</span><span class="sxs-lookup"><span data-stu-id="526ab-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="526ab-104">Bu bağlamda bir *ayarı* herhangi belirli uygulama veya belirli kullanıcı için geçerli olabilecek bilgidir — herhangi bir şeyin bir veritabanı bağlantı dizesi kullanıcıya varsayılan pencere boyutu tercih edilen.</span><span class="sxs-lookup"><span data-stu-id="526ab-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="526ab-105">Varsayılan olarak, bir Windows Forms uygulamasında uygulama ayarları kullanan <xref:System.Configuration.LocalFileSettingsProvider> .NET yapılandırma sistemini ayarları bir XML yapılandırma dosyasında depolamak için kullandığı sınıf.</span><span class="sxs-lookup"><span data-stu-id="526ab-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="526ab-106">Uygulama ayarları tarafından kullanılan dosyaları hakkında daha fazla bilgi için bkz: [uygulama ayarları mimarisi](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="526ab-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="526ab-107">Uygulama ayarları aşağıdaki öğeleri kullanır yapılandırma dosyalarını bir parçası olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="526ab-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="526ab-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="526ab-108">Element</span></span>                    | <span data-ttu-id="526ab-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="526ab-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="526ab-110">**\<applicationSettings >**</span><span class="sxs-lookup"><span data-stu-id="526ab-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="526ab-111">Tüm içeren  **\<ayarı >** etiketler uygulamaya özgü.</span><span class="sxs-lookup"><span data-stu-id="526ab-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="526ab-112">**\<kullanıcı ayarlarını >**</span><span class="sxs-lookup"><span data-stu-id="526ab-112">**\<userSettings>**</span></span>        | <span data-ttu-id="526ab-113">Tüm içeren  **\<ayarı >** geçerli kullanıcıya özel etiketler.</span><span class="sxs-lookup"><span data-stu-id="526ab-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="526ab-114">**\<Ayar >**</span><span class="sxs-lookup"><span data-stu-id="526ab-114">**\<setting>**</span></span>             | <span data-ttu-id="526ab-115">Bir ayar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="526ab-115">Defines a setting.</span></span> <span data-ttu-id="526ab-116">Ya da alt  **\<applicationSettings >** veya  **\<ayarlarını >**.</span><span class="sxs-lookup"><span data-stu-id="526ab-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="526ab-117">**\<Değer >**</span><span class="sxs-lookup"><span data-stu-id="526ab-117">**\<value>**</span></span>               | <span data-ttu-id="526ab-118">Bir ayarın değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="526ab-118">Defines a setting's value.</span></span> <span data-ttu-id="526ab-119">Alt  **\<ayarı >**.</span><span class="sxs-lookup"><span data-stu-id="526ab-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="526ab-120">\<applicationSettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="526ab-120">\<applicationSettings> element</span></span>

<span data-ttu-id="526ab-121">Bu öğe tüm içeren  **\<ayarı >** bir istemci bilgisayarda uygulama örneği için özel etiketler.</span><span class="sxs-lookup"><span data-stu-id="526ab-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="526ab-122">Öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="526ab-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="526ab-123">\<kullanıcı ayarlarını > öğesi</span><span class="sxs-lookup"><span data-stu-id="526ab-123">\<userSettings> element</span></span>

<span data-ttu-id="526ab-124">Bu öğe tüm içeren  **\<ayarı >** uygulamayı kullanmakta olduğu kullanıcı için özel etiketler.</span><span class="sxs-lookup"><span data-stu-id="526ab-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="526ab-125">Öznitelikleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="526ab-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="526ab-126">\<Ayarlama > öğesi</span><span class="sxs-lookup"><span data-stu-id="526ab-126">\<setting> element</span></span>

<span data-ttu-id="526ab-127">Bu öğe bir ayar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="526ab-127">This element defines a setting.</span></span> <span data-ttu-id="526ab-128">Aşağıdaki özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="526ab-128">It has the following attributes.</span></span>

| <span data-ttu-id="526ab-129">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="526ab-129">Attribute</span></span>        | <span data-ttu-id="526ab-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="526ab-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="526ab-131">**adı**</span><span class="sxs-lookup"><span data-stu-id="526ab-131">**name**</span></span>         | <span data-ttu-id="526ab-132">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="526ab-132">Required.</span></span> <span data-ttu-id="526ab-133">Ayar benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="526ab-133">The unique ID of the setting.</span></span> <span data-ttu-id="526ab-134">Visual Studio oluşturulan ayarları adıyla kaydedilir `ProjectName.Properties.Settings`.</span><span class="sxs-lookup"><span data-stu-id="526ab-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="526ab-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="526ab-135">**serializedAs**</span></span> | <span data-ttu-id="526ab-136">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="526ab-136">Required.</span></span> <span data-ttu-id="526ab-137">Metin değeri serileştirmek için kullanılacak biçimi.</span><span class="sxs-lookup"><span data-stu-id="526ab-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="526ab-138">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="526ab-138">Valid values are:</span></span><br><br><span data-ttu-id="526ab-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="526ab-139">- `string`.</span></span> <span data-ttu-id="526ab-140">Değer olarak dizesi kullanılarak serileştirilmiş bir <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="526ab-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="526ab-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="526ab-141">- `xml`.</span></span> <span data-ttu-id="526ab-142">Değer XML serileştirme kullanarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="526ab-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="526ab-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="526ab-143">- `binary`.</span></span> <span data-ttu-id="526ab-144">Değer ikili serileştirme kullanılarak metin ile kodlanmış ikili olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="526ab-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="526ab-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="526ab-145">- `custom`.</span></span> <span data-ttu-id="526ab-146">Ayarlar sağlayıcısı serileştiren bilgiyi bu ayarın sahiptir ve XML'deki serileştirir.</span><span class="sxs-lookup"><span data-stu-id="526ab-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="526ab-147">\<Değer > öğesi</span><span class="sxs-lookup"><span data-stu-id="526ab-147">\<value> element</span></span>

<span data-ttu-id="526ab-148">Bu öğe bir ayarın değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="526ab-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="526ab-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="526ab-149">Example</span></span>

<span data-ttu-id="526ab-150">Aşağıdaki örnekte, iki uygulama kapsamlı ve iki kullanıcı kapsamlı ayarlarını tanımlayan uygulama ayarları dosyası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="526ab-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="526ab-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="526ab-151">See also</span></span>

<span data-ttu-id="526ab-152">[Uygulama ayarlarına genel bakış](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="526ab-152">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="526ab-153">Uygulama ayarları mimarisi</span><span class="sxs-lookup"><span data-stu-id="526ab-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
