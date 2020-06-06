---
title: Uygulama ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81242835"
---
# <a name="application-settings-schema"></a><span data-ttu-id="6eb4c-102">Uygulama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6eb4c-102">Application Settings schema</span></span>

<span data-ttu-id="6eb4c-103">Uygulama ayarları bir Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasına ve almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="6eb4c-104">Bu bağlamda, bir *ayar* , uygulamaya özgü veya geçerli kullanıcıya özgü olabilecek herhangi bir bilgi olan bir veritabanı bağlantı dizesinden kullanıcının tercih edilen varsayılan pencere boyutuna kadar her şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="6eb4c-105">Varsayılan olarak, bir Windows Forms uygulamasındaki uygulama ayarları, <xref:System.Configuration.LocalFileSettingsProvider> ayarları BIR XML yapılandırma dosyasında depolamak için .NET yapılandırma sistemini kullanan sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="6eb4c-106">Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="6eb4c-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="6eb4c-107">Uygulama ayarları, kullandığı yapılandırma dosyalarının bir parçası olarak aşağıdaki öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="6eb4c-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="6eb4c-108">Element</span></span>                    | <span data-ttu-id="6eb4c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6eb4c-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="6eb4c-110">**\<setting>** Uygulamaya özgü tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-110">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="6eb4c-111">**\<setting>** Geçerli kullanıcıya özgü tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-111">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="6eb4c-112">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-112">Defines a setting.</span></span> <span data-ttu-id="6eb4c-113">Ya da alt **\<applicationSettings>** öğesi **\<userSettings>** .</span><span class="sxs-lookup"><span data-stu-id="6eb4c-113">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="6eb4c-114">Bir ayarın değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-114">Defines a setting's value.</span></span> <span data-ttu-id="6eb4c-115">Alt öğesi **\<setting>** .</span><span class="sxs-lookup"><span data-stu-id="6eb4c-115">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="6eb4c-116">\<applicationSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="6eb4c-116">\<applicationSettings> element</span></span>

<span data-ttu-id="6eb4c-117">Bu öğe **\<setting>** , bir istemci bilgisayarındaki uygulamanın bir örneğine özgü olan tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-117">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="6eb4c-118">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-118">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="6eb4c-119">\<userSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="6eb4c-119">\<userSettings> element</span></span>

<span data-ttu-id="6eb4c-120">Bu öğe, **\<setting>** Şu anda uygulamayı kullanan kullanıcıya özgü tüm etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-120">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="6eb4c-121">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-121">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="6eb4c-122">\<setting> öğesi</span><span class="sxs-lookup"><span data-stu-id="6eb4c-122">\<setting> element</span></span>

<span data-ttu-id="6eb4c-123">Bu öğe bir ayar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-123">This element defines a setting.</span></span> <span data-ttu-id="6eb4c-124">Aşağıdaki özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-124">It has the following attributes.</span></span>

| <span data-ttu-id="6eb4c-125">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6eb4c-125">Attribute</span></span>        | <span data-ttu-id="6eb4c-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6eb4c-126">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="6eb4c-127">**ada**</span><span class="sxs-lookup"><span data-stu-id="6eb4c-127">**name**</span></span>         | <span data-ttu-id="6eb4c-128">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-128">Required.</span></span> <span data-ttu-id="6eb4c-129">Ayarın benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-129">The unique ID of the setting.</span></span> <span data-ttu-id="6eb4c-130">Visual Studio ile oluşturulan ayarlar, adıyla birlikte kaydedilir `ProjectName.Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="6eb4c-130">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="6eb4c-131">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="6eb4c-131">**serializeAs**</span></span> | <span data-ttu-id="6eb4c-132">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-132">Required.</span></span> <span data-ttu-id="6eb4c-133">Değerin metin olarak serileştirilmesi için kullanılacak biçim.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-133">The format to use for serializing the value to text.</span></span> <span data-ttu-id="6eb4c-134">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="6eb4c-134">Valid values are:</span></span><br><br><span data-ttu-id="6eb4c-135">- `string`.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-135">- `string`.</span></span> <span data-ttu-id="6eb4c-136">Değer, kullanarak bir dize olarak serileştirilir <xref:System.ComponentModel.TypeConverter> .</span><span class="sxs-lookup"><span data-stu-id="6eb4c-136">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="6eb4c-137">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-137">- `xml`.</span></span> <span data-ttu-id="6eb4c-138">Değer XML serileştirme kullanılarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-138">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="6eb4c-139">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-139">- `binary`.</span></span> <span data-ttu-id="6eb4c-140">Değer, ikili serileştirme kullanılarak metin kodlu ikili olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-140">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="6eb4c-141">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-141">- `custom`.</span></span> <span data-ttu-id="6eb4c-142">Ayarlar sağlayıcısı bu ayar hakkında bilgi sahibi ve serileştirildikleri ve serileştirildikleri.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-142">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="6eb4c-143">\<value> öğesi</span><span class="sxs-lookup"><span data-stu-id="6eb4c-143">\<value> element</span></span>

<span data-ttu-id="6eb4c-144">Bu öğe bir ayarın değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-144">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="6eb4c-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="6eb4c-145">Example</span></span>

<span data-ttu-id="6eb4c-146">Aşağıdaki örnek, uygulama kapsamlı iki ayarı ve kullanıcı kapsamlı iki ayarı tanımlayan bir uygulama ayarları dosyası gösterir:</span><span class="sxs-lookup"><span data-stu-id="6eb4c-146">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6eb4c-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6eb4c-147">See also</span></span>

- [<span data-ttu-id="6eb4c-148">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6eb4c-148">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="6eb4c-149">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="6eb4c-149">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
