---
title: Uygulama ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: fc9cd8ac3819c6a02019c871e7bd45ceb4c2cef7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552316"
---
# <a name="application-settings-schema"></a><span data-ttu-id="1401a-102">Uygulama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="1401a-102">Application Settings schema</span></span>

<span data-ttu-id="1401a-103">Uygulama ayarları bir Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasına ve almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="1401a-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="1401a-104">Bu bağlamda, bir *ayar* , uygulamaya özgü veya geçerli kullanıcıya özgü olabilecek herhangi bir bilgi olan bir veritabanı bağlantı dizesinden kullanıcının tercih edilen varsayılan pencere boyutuna kadar her şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="1401a-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="1401a-105">Varsayılan olarak, bir Windows Forms uygulamasındaki uygulama ayarları, <xref:System.Configuration.LocalFileSettingsProvider> ayarları BIR XML yapılandırma dosyasında depolamak için .NET yapılandırma sistemini kullanan sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1401a-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="1401a-106">Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](/dotnet/desktop/winforms/advanced/application-settings-architecture).</span><span class="sxs-lookup"><span data-stu-id="1401a-106">For more information about the files used by application settings, see [Application Settings Architecture](/dotnet/desktop/winforms/advanced/application-settings-architecture).</span></span>

<span data-ttu-id="1401a-107">Uygulama ayarları, kullandığı yapılandırma dosyalarının bir parçası olarak aşağıdaki öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1401a-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="1401a-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="1401a-108">Element</span></span>                    | <span data-ttu-id="1401a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1401a-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="1401a-110">**\<setting>** Uygulamaya özgü tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1401a-110">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="1401a-111">**\<setting>** Geçerli kullanıcıya özgü tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1401a-111">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="1401a-112">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1401a-112">Defines a setting.</span></span> <span data-ttu-id="1401a-113">Ya da alt **\<applicationSettings>** öğesi **\<userSettings>** .</span><span class="sxs-lookup"><span data-stu-id="1401a-113">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="1401a-114">Bir ayarın değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1401a-114">Defines a setting's value.</span></span> <span data-ttu-id="1401a-115">Alt öğesi **\<setting>** .</span><span class="sxs-lookup"><span data-stu-id="1401a-115">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="1401a-116">\<applicationSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="1401a-116">\<applicationSettings> element</span></span>

<span data-ttu-id="1401a-117">Bu öğe **\<setting>** , bir istemci bilgisayarındaki uygulamanın bir örneğine özgü olan tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1401a-117">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="1401a-118">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="1401a-118">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="1401a-119">\<userSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="1401a-119">\<userSettings> element</span></span>

<span data-ttu-id="1401a-120">Bu öğe, **\<setting>** Şu anda uygulamayı kullanan kullanıcıya özgü tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1401a-120">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="1401a-121">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="1401a-121">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="1401a-122">\<setting> öğesi</span><span class="sxs-lookup"><span data-stu-id="1401a-122">\<setting> element</span></span>

<span data-ttu-id="1401a-123">Bu öğe bir ayar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1401a-123">This element defines a setting.</span></span> <span data-ttu-id="1401a-124">Aşağıdaki özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1401a-124">It has the following attributes.</span></span>

| <span data-ttu-id="1401a-125">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1401a-125">Attribute</span></span>        | <span data-ttu-id="1401a-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1401a-126">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="1401a-127">**ada**</span><span class="sxs-lookup"><span data-stu-id="1401a-127">**name**</span></span>         | <span data-ttu-id="1401a-128">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1401a-128">Required.</span></span> <span data-ttu-id="1401a-129">Ayarın benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1401a-129">The unique ID of the setting.</span></span> <span data-ttu-id="1401a-130">Visual Studio ile oluşturulan ayarlar, adıyla birlikte kaydedilir `ProjectName.Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="1401a-130">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="1401a-131">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="1401a-131">**serializeAs**</span></span> | <span data-ttu-id="1401a-132">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1401a-132">Required.</span></span> <span data-ttu-id="1401a-133">Değerin metin olarak serileştirilmesi için kullanılacak biçim.</span><span class="sxs-lookup"><span data-stu-id="1401a-133">The format to use for serializing the value to text.</span></span> <span data-ttu-id="1401a-134">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="1401a-134">Valid values are:</span></span><br><br><span data-ttu-id="1401a-135">- `string`.</span><span class="sxs-lookup"><span data-stu-id="1401a-135">- `string`.</span></span> <span data-ttu-id="1401a-136">Değer, kullanarak bir dize olarak serileştirilir <xref:System.ComponentModel.TypeConverter> .</span><span class="sxs-lookup"><span data-stu-id="1401a-136">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="1401a-137">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="1401a-137">- `xml`.</span></span> <span data-ttu-id="1401a-138">Değer XML serileştirme kullanılarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="1401a-138">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="1401a-139">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="1401a-139">- `binary`.</span></span> <span data-ttu-id="1401a-140">Değer, ikili serileştirme kullanılarak metin kodlu ikili olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="1401a-140">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="1401a-141">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="1401a-141">- `custom`.</span></span> <span data-ttu-id="1401a-142">Ayarlar sağlayıcısı bu ayar hakkında bilgi sahibi ve serileştirildikleri ve serileştirildikleri.</span><span class="sxs-lookup"><span data-stu-id="1401a-142">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="1401a-143">\<value> öğesi</span><span class="sxs-lookup"><span data-stu-id="1401a-143">\<value> element</span></span>

<span data-ttu-id="1401a-144">Bu öğe bir ayarın değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1401a-144">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="1401a-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="1401a-145">Example</span></span>

<span data-ttu-id="1401a-146">Aşağıdaki örnek, uygulama kapsamlı iki ayarı ve kullanıcı kapsamlı iki ayarı tanımlayan bir uygulama ayarları dosyası gösterir:</span><span class="sxs-lookup"><span data-stu-id="1401a-146">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1401a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1401a-147">See also</span></span>

- [<span data-ttu-id="1401a-148">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1401a-148">Application Settings Overview</span></span>](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [<span data-ttu-id="1401a-149">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="1401a-149">Application Settings Architecture</span></span>](/dotnet/desktop/winforms/advanced/application-settings-architecture)
