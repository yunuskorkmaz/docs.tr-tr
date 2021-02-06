---
description: 'Daha fazla bilgi edinin: uygulama ayarları şeması'
title: Uygulama ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 24c5771e9d98d07bbdc8dab5fce0f1535bc9b582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652906"
---
# <a name="application-settings-schema"></a><span data-ttu-id="d62c2-103">Uygulama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="d62c2-103">Application Settings schema</span></span>

<span data-ttu-id="d62c2-104">Uygulama ayarları bir Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasına ve almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-104">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="d62c2-105">Bu bağlamda, bir *ayar* , uygulamaya özgü veya geçerli kullanıcıya özgü olabilecek herhangi bir bilgi olan bir veritabanı bağlantı dizesinden kullanıcının tercih edilen varsayılan pencere boyutuna kadar her şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-105">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="d62c2-106">Varsayılan olarak, bir Windows Forms uygulamasındaki uygulama ayarları, <xref:System.Configuration.LocalFileSettingsProvider> ayarları BIR XML yapılandırma dosyasında depolamak için .NET yapılandırma sistemini kullanan sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d62c2-106">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="d62c2-107">Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](/dotnet/desktop/winforms/advanced/application-settings-architecture).</span><span class="sxs-lookup"><span data-stu-id="d62c2-107">For more information about the files used by application settings, see [Application Settings Architecture](/dotnet/desktop/winforms/advanced/application-settings-architecture).</span></span>

<span data-ttu-id="d62c2-108">Uygulama ayarları, kullandığı yapılandırma dosyalarının bir parçası olarak aşağıdaki öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d62c2-108">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="d62c2-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="d62c2-109">Element</span></span>                    | <span data-ttu-id="d62c2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d62c2-110">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="d62c2-111">**\<setting>** Uygulamaya özgü tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="d62c2-112">**\<setting>** Geçerli kullanıcıya özgü tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-112">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="d62c2-113">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d62c2-113">Defines a setting.</span></span> <span data-ttu-id="d62c2-114">Ya da alt **\<applicationSettings>** öğesi **\<userSettings>** .</span><span class="sxs-lookup"><span data-stu-id="d62c2-114">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="d62c2-115">Bir ayarın değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d62c2-115">Defines a setting's value.</span></span> <span data-ttu-id="d62c2-116">Alt öğesi **\<setting>** .</span><span class="sxs-lookup"><span data-stu-id="d62c2-116">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="d62c2-117">\<applicationSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="d62c2-117">\<applicationSettings> element</span></span>

<span data-ttu-id="d62c2-118">Bu öğe **\<setting>** , bir istemci bilgisayarındaki uygulamanın bir örneğine özgü olan tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-118">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="d62c2-119">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d62c2-119">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="d62c2-120">\<userSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="d62c2-120">\<userSettings> element</span></span>

<span data-ttu-id="d62c2-121">Bu öğe, **\<setting>** Şu anda uygulamayı kullanan kullanıcıya özgü tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-121">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="d62c2-122">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d62c2-122">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="d62c2-123">\<setting> öğesi</span><span class="sxs-lookup"><span data-stu-id="d62c2-123">\<setting> element</span></span>

<span data-ttu-id="d62c2-124">Bu öğe bir ayar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d62c2-124">This element defines a setting.</span></span> <span data-ttu-id="d62c2-125">Aşağıdaki özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-125">It has the following attributes.</span></span>

| <span data-ttu-id="d62c2-126">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d62c2-126">Attribute</span></span>        | <span data-ttu-id="d62c2-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d62c2-127">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="d62c2-128">**ada**</span><span class="sxs-lookup"><span data-stu-id="d62c2-128">**name**</span></span>         | <span data-ttu-id="d62c2-129">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-129">Required.</span></span> <span data-ttu-id="d62c2-130">Ayarın benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d62c2-130">The unique ID of the setting.</span></span> <span data-ttu-id="d62c2-131">Visual Studio ile oluşturulan ayarlar, adıyla birlikte kaydedilir `ProjectName.Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="d62c2-131">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="d62c2-132">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="d62c2-132">**serializeAs**</span></span> | <span data-ttu-id="d62c2-133">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-133">Required.</span></span> <span data-ttu-id="d62c2-134">Değerin metin olarak serileştirilmesi için kullanılacak biçim.</span><span class="sxs-lookup"><span data-stu-id="d62c2-134">The format to use for serializing the value to text.</span></span> <span data-ttu-id="d62c2-135">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="d62c2-135">Valid values are:</span></span><br><br><span data-ttu-id="d62c2-136">- `string`.</span><span class="sxs-lookup"><span data-stu-id="d62c2-136">- `string`.</span></span> <span data-ttu-id="d62c2-137">Değer, kullanarak bir dize olarak serileştirilir <xref:System.ComponentModel.TypeConverter> .</span><span class="sxs-lookup"><span data-stu-id="d62c2-137">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="d62c2-138">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="d62c2-138">- `xml`.</span></span> <span data-ttu-id="d62c2-139">Değer XML serileştirme kullanılarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-139">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="d62c2-140">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="d62c2-140">- `binary`.</span></span> <span data-ttu-id="d62c2-141">Değer, ikili serileştirme kullanılarak metin kodlu ikili olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-141">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="d62c2-142">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="d62c2-142">- `custom`.</span></span> <span data-ttu-id="d62c2-143">Ayarlar sağlayıcısı bu ayar hakkında bilgi sahibi ve serileştirildikleri ve serileştirildikleri.</span><span class="sxs-lookup"><span data-stu-id="d62c2-143">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="d62c2-144">\<value> öğesi</span><span class="sxs-lookup"><span data-stu-id="d62c2-144">\<value> element</span></span>

<span data-ttu-id="d62c2-145">Bu öğe bir ayarın değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d62c2-145">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="d62c2-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="d62c2-146">Example</span></span>

<span data-ttu-id="d62c2-147">Aşağıdaki örnek, uygulama kapsamlı iki ayarı ve kullanıcı kapsamlı iki ayarı tanımlayan bir uygulama ayarları dosyası gösterir:</span><span class="sxs-lookup"><span data-stu-id="d62c2-147">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d62c2-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d62c2-148">See also</span></span>

- [<span data-ttu-id="d62c2-149">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d62c2-149">Application Settings Overview</span></span>](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [<span data-ttu-id="d62c2-150">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="d62c2-150">Application Settings Architecture</span></span>](/dotnet/desktop/winforms/advanced/application-settings-architecture)
