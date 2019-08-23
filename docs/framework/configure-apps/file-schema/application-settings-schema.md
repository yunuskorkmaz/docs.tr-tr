---
title: Uygulama ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 89a08434332b0242fe57e9dcaa3b3ebcc5692d06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927757"
---
# <a name="application-settings-schema"></a><span data-ttu-id="dca02-102">Uygulama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="dca02-102">Application Settings schema</span></span>

<span data-ttu-id="dca02-103">Uygulama ayarları bir Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasına ve almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="dca02-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="dca02-104">Bu bağlamda, bir *ayar* , uygulamaya özgü veya geçerli kullanıcıya özgü olabilecek herhangi bir bilgi olan bir veritabanı bağlantı dizesinden kullanıcının tercih edilen varsayılan pencere boyutuna kadar her şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="dca02-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="dca02-105">Varsayılan olarak, bir Windows Forms uygulamasındaki uygulama ayarları, ayarları bir <xref:System.Configuration.LocalFileSettingsProvider> XML yapılandırma dosyasında depolamak için .NET yapılandırma sistemini kullanan sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="dca02-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="dca02-106">Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="dca02-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="dca02-107">Uygulama ayarları, kullandığı yapılandırma dosyalarının bir parçası olarak aşağıdaki öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dca02-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="dca02-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="dca02-108">Element</span></span>                    | <span data-ttu-id="dca02-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dca02-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="dca02-110">**\<applicationSettings >**</span><span class="sxs-lookup"><span data-stu-id="dca02-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="dca02-111">Uygulamaya özgü tüm  **\<ayar >** etiketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="dca02-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="dca02-112">**\<userSettings >**</span><span class="sxs-lookup"><span data-stu-id="dca02-112">**\<userSettings>**</span></span>        | <span data-ttu-id="dca02-113">Geçerli kullanıcıya özgü tüm  **\<ayar >** etiketlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="dca02-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="dca02-114">**\<> ayarlama**</span><span class="sxs-lookup"><span data-stu-id="dca02-114">**\<setting>**</span></span>             | <span data-ttu-id="dca02-115">Bir ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dca02-115">Defines a setting.</span></span> <span data-ttu-id="dca02-116">**\<ApplicationSettings >** ya  **\<da UserSettings >** alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="dca02-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="dca02-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="dca02-117">**\<value>**</span></span>               | <span data-ttu-id="dca02-118">Bir ayarın değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dca02-118">Defines a setting's value.</span></span> <span data-ttu-id="dca02-119">> Ayarının alt öğesi.  **\<**</span><span class="sxs-lookup"><span data-stu-id="dca02-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="dca02-120">\<applicationSettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="dca02-120">\<applicationSettings> element</span></span>

<span data-ttu-id="dca02-121">Bu öğe, bir istemci bilgisayarında uygulamanın bir örneğine özgü  **\<> Tüm ayarı** içerir.</span><span class="sxs-lookup"><span data-stu-id="dca02-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="dca02-122">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="dca02-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="dca02-123">\<userSettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="dca02-123">\<userSettings> element</span></span>

<span data-ttu-id="dca02-124">Bu öğe, şu anda uygulamayı kullanan kullanıcıya özgü tüm  **\<ayar > ayarlarını** içerir.</span><span class="sxs-lookup"><span data-stu-id="dca02-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="dca02-125">Hiçbir öznitelik tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="dca02-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="dca02-126">\<> öğesi ayarlanıyor</span><span class="sxs-lookup"><span data-stu-id="dca02-126">\<setting> element</span></span>

<span data-ttu-id="dca02-127">Bu öğe bir ayar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dca02-127">This element defines a setting.</span></span> <span data-ttu-id="dca02-128">Aşağıdaki özniteliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="dca02-128">It has the following attributes.</span></span>

| <span data-ttu-id="dca02-129">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dca02-129">Attribute</span></span>        | <span data-ttu-id="dca02-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dca02-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="dca02-131">**name**</span><span class="sxs-lookup"><span data-stu-id="dca02-131">**name**</span></span>         | <span data-ttu-id="dca02-132">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="dca02-132">Required.</span></span> <span data-ttu-id="dca02-133">Ayarın benzersiz KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dca02-133">The unique ID of the setting.</span></span> <span data-ttu-id="dca02-134">Visual Studio ile oluşturulan ayarlar, adıyla `ProjectName.Properties.Settings`birlikte kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="dca02-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="dca02-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="dca02-135">**serializedAs**</span></span> | <span data-ttu-id="dca02-136">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="dca02-136">Required.</span></span> <span data-ttu-id="dca02-137">Değerin metin olarak serileştirilmesi için kullanılacak biçim.</span><span class="sxs-lookup"><span data-stu-id="dca02-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="dca02-138">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dca02-138">Valid values are:</span></span><br><br><span data-ttu-id="dca02-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="dca02-139">- `string`.</span></span> <span data-ttu-id="dca02-140">Değer, kullanarak <xref:System.ComponentModel.TypeConverter>bir dize olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="dca02-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="dca02-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="dca02-141">- `xml`.</span></span> <span data-ttu-id="dca02-142">Değer XML serileştirme kullanılarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="dca02-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="dca02-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="dca02-143">- `binary`.</span></span> <span data-ttu-id="dca02-144">Değer, ikili serileştirme kullanılarak metin kodlu ikili olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="dca02-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="dca02-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="dca02-145">- `custom`.</span></span> <span data-ttu-id="dca02-146">Ayarlar sağlayıcısı bu ayar hakkında bilgi sahibi ve serileştirildikleri ve serileştirildikleri.</span><span class="sxs-lookup"><span data-stu-id="dca02-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="dca02-147">\<değer > öğesi</span><span class="sxs-lookup"><span data-stu-id="dca02-147">\<value> element</span></span>

<span data-ttu-id="dca02-148">Bu öğe bir ayarın değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="dca02-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="dca02-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="dca02-149">Example</span></span>

<span data-ttu-id="dca02-150">Aşağıdaki örnek, uygulama kapsamlı iki ayarı ve kullanıcı kapsamlı iki ayarı tanımlayan bir uygulama ayarları dosyası gösterir:</span><span class="sxs-lookup"><span data-stu-id="dca02-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dca02-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dca02-151">See also</span></span>

- [<span data-ttu-id="dca02-152">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dca02-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="dca02-153">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="dca02-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
