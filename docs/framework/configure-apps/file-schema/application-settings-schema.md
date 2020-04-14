---
title: Uygulama Ayarları şema
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242835"
---
# <a name="application-settings-schema"></a><span data-ttu-id="9d7ef-102">Uygulama Ayarları şema</span><span class="sxs-lookup"><span data-stu-id="9d7ef-102">Application Settings schema</span></span>

<span data-ttu-id="9d7ef-103">Uygulama ayarları, windows formları veya ASP.NET uygulamasının uygulama kapsamı ve kullanıcı kapsamı namına ayarları depolamasına ve almasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="9d7ef-104">Bu bağlamda, *ayar,* uygulamaya özgü veya geçerli kullanıcıya özgü olabilecek herhangi bir bilgi parçasıdır — veritabanı bağlantı dizesinden kullanıcının tercih edilen varsayılan pencere boyutuna kadar her şey.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="9d7ef-105">Varsayılan olarak, Windows Forms uygulamasındaki <xref:System.Configuration.LocalFileSettingsProvider> uygulama ayarları, bir XML yapılandırma dosyasında ayarları depolamak için .NET yapılandırma sistemini kullanan sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="9d7ef-106">Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için [Uygulama Ayarları Mimarisi'ne](../../winforms/advanced/application-settings-architecture.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="9d7ef-107">Uygulama ayarları, kullandığı yapılandırma dosyalarının bir parçası olarak aşağıdaki öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="9d7ef-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="9d7ef-108">Element</span></span>                    | <span data-ttu-id="9d7ef-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d7ef-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="9d7ef-110">**\<applicationAyarlar>**</span><span class="sxs-lookup"><span data-stu-id="9d7ef-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="9d7ef-111">Uygulamaya \*\* \<\*\* özgü tüm ayar>etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="9d7ef-112">**\<userAyarlar>**</span><span class="sxs-lookup"><span data-stu-id="9d7ef-112">**\<userSettings>**</span></span>        | <span data-ttu-id="9d7ef-113">Geçerli \*\* \<kullanıcıya\*\* özgü tüm ayarları>etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="9d7ef-114">**\<>ayarlama**</span><span class="sxs-lookup"><span data-stu-id="9d7ef-114">**\<setting>**</span></span>             | <span data-ttu-id="9d7ef-115">Bir ayar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-115">Defines a setting.</span></span> <span data-ttu-id="9d7ef-116">Uygulamanın alt>\*\* \<veya\*\* \*\* \<kullanıcıAyarlar>. \*\*</span><span class="sxs-lookup"><span data-stu-id="9d7ef-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="9d7ef-117">**\<değer>**</span><span class="sxs-lookup"><span data-stu-id="9d7ef-117">**\<value>**</span></span>               | <span data-ttu-id="9d7ef-118">Ayarın değerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-118">Defines a setting's value.</span></span> <span data-ttu-id="9d7ef-119">>\*\* \<ayar \*\*Çocuk .</span><span class="sxs-lookup"><span data-stu-id="9d7ef-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="9d7ef-120">\<applicationAyarlar> öğesi</span><span class="sxs-lookup"><span data-stu-id="9d7ef-120">\<applicationSettings> element</span></span>

<span data-ttu-id="9d7ef-121">Bu öğe, \*\* \<\*\* istemci bilgisayarda uygulamanın bir örneğine özgü tüm ayar>etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="9d7ef-122">Hiçbir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="9d7ef-123">\<userAyarlar> öğesi</span><span class="sxs-lookup"><span data-stu-id="9d7ef-123">\<userSettings> element</span></span>

<span data-ttu-id="9d7ef-124">Bu öğe, \*\* \<\*\* uygulamayı şu anda kullanmakta olan kullanıcıya özgü tüm ayar>etiketleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="9d7ef-125">Hiçbir öznitelik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="9d7ef-126">\<> öğesi ayarlama</span><span class="sxs-lookup"><span data-stu-id="9d7ef-126">\<setting> element</span></span>

<span data-ttu-id="9d7ef-127">Bu öğe bir ayar tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-127">This element defines a setting.</span></span> <span data-ttu-id="9d7ef-128">Aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-128">It has the following attributes.</span></span>

| <span data-ttu-id="9d7ef-129">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9d7ef-129">Attribute</span></span>        | <span data-ttu-id="9d7ef-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d7ef-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="9d7ef-131">**Adı**</span><span class="sxs-lookup"><span data-stu-id="9d7ef-131">**name**</span></span>         | <span data-ttu-id="9d7ef-132">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-132">Required.</span></span> <span data-ttu-id="9d7ef-133">Ayarın benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-133">The unique ID of the setting.</span></span> <span data-ttu-id="9d7ef-134">Visual Studio aracılığıyla oluşturulan ayarlar `ProjectName.Properties.Settings`adıyla kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="9d7ef-135">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="9d7ef-135">**serializeAs**</span></span> | <span data-ttu-id="9d7ef-136">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-136">Required.</span></span> <span data-ttu-id="9d7ef-137">Metne değeri serihale getirmek için kullanılacak biçim.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="9d7ef-138">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="9d7ef-138">Valid values are:</span></span><br><br><span data-ttu-id="9d7ef-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-139">- `string`.</span></span> <span data-ttu-id="9d7ef-140">Değer bir dize olarak serihale edilir. <xref:System.ComponentModel.TypeConverter></span><span class="sxs-lookup"><span data-stu-id="9d7ef-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="9d7ef-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-141">- `xml`.</span></span> <span data-ttu-id="9d7ef-142">Değer XML serileştirme kullanılarak seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="9d7ef-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-143">- `binary`.</span></span> <span data-ttu-id="9d7ef-144">Değer, ikili serileştirme kullanılarak metin kodlu ikili olarak serihale edilir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="9d7ef-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-145">- `custom`.</span></span> <span data-ttu-id="9d7ef-146">Ayarlar sağlayıcısı bu ayarı doğal bilgiye sahiptir ve serihale eder ve de-serializes.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="9d7ef-147">\<değer> öğesi</span><span class="sxs-lookup"><span data-stu-id="9d7ef-147">\<value> element</span></span>

<span data-ttu-id="9d7ef-148">Bu öğe bir ayarın değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="9d7ef-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d7ef-149">Example</span></span>

<span data-ttu-id="9d7ef-150">Aşağıdaki örnekte, uygulama kapsamı içinde iki ayar ve iki kullanıcı kapsamı ayarı tanımlayan bir uygulama ayarları dosyası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9d7ef-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9d7ef-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d7ef-151">See also</span></span>

- [<span data-ttu-id="9d7ef-152">Uygulama Ayarlarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d7ef-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="9d7ef-153">Uygulama Ayarları Mimarisi</span><span class="sxs-lookup"><span data-stu-id="9d7ef-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
