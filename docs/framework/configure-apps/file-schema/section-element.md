---
title: <section> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153742"
---
# <a name="section-element"></a><span data-ttu-id="fe26c-102">\<bölüm> öğesi</span><span class="sxs-lookup"><span data-stu-id="fe26c-102">\<section> element</span></span>

<span data-ttu-id="fe26c-103">Yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="fe26c-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="fe26c-104">[**\<yapılandırma>**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe26c-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="fe26c-105">&nbsp;&nbsp;[**\<configBölüm>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="fe26c-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="fe26c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<bölüm>**</span><span class="sxs-lookup"><span data-stu-id="fe26c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="fe26c-107">[**\<yapılandırma>**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe26c-107">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="fe26c-108">&nbsp;&nbsp;[**\<configBölüm>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="fe26c-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="fe26c-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bölümGrup>**](sectiongroup-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="fe26c-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>\
<span data-ttu-id="fe26c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bölüm>**</span><span class="sxs-lookup"><span data-stu-id="fe26c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fe26c-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe26c-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="fe26c-112">Gerekli öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe26c-112">Required attributes</span></span>

|           | <span data-ttu-id="fe26c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe26c-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="fe26c-114">**Adı**</span><span class="sxs-lookup"><span data-stu-id="fe26c-114">**name**</span></span>  | <span data-ttu-id="fe26c-115">Yapılandırma bölümünün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe26c-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="fe26c-116">**Türü**</span><span class="sxs-lookup"><span data-stu-id="fe26c-116">**type**</span></span>  | <span data-ttu-id="fe26c-117">Yapılandırma dosyasından bölümü okuyan yapılandırma bölümü işleyicisınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe26c-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="fe26c-118">Tür değeri sözdizimi vardır "tam nitelikli-bölüm işleyicisi-sınıf adı, basit-derleme-adı".</span><span class="sxs-lookup"><span data-stu-id="fe26c-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="fe26c-119">Basit derleme adı *.dll* dosya uzantısı olmayan kök dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="fe26c-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="fe26c-120">İsteğe bağlı öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe26c-120">Optional attributes</span></span>

<span data-ttu-id="fe26c-121">Aşağıdaki öznitelikler yalnızca ASP.NET uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fe26c-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="fe26c-122">Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="fe26c-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="fe26c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe26c-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="fe26c-124">**Allowdefinition**</span><span class="sxs-lookup"><span data-stu-id="fe26c-124">**allowDefinition**</span></span> | <span data-ttu-id="fe26c-125">Bölümün hangi yapılandırma dosyasında kullanılabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe26c-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="fe26c-126">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="fe26c-126">Use one of the following values:</span></span><br><br><span data-ttu-id="fe26c-127">**Heryer -de**</span><span class="sxs-lookup"><span data-stu-id="fe26c-127">**Everywhere**</span></span><br><span data-ttu-id="fe26c-128">Bölümün herhangi bir yapılandırma dosyasında kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe26c-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="fe26c-129">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="fe26c-129">This is the default.</span></span><br><span data-ttu-id="fe26c-130">**MakineSadece**</span><span class="sxs-lookup"><span data-stu-id="fe26c-130">**MachineOnly**</span></span><br><span data-ttu-id="fe26c-131">Bölümün yalnızca makine yapılandırma dosyasında *(Machine.config)* kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe26c-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="fe26c-132">**MachinetoApplication**</span><span class="sxs-lookup"><span data-stu-id="fe26c-132">**MachineToApplication**</span></span><br><span data-ttu-id="fe26c-133">Bölümün makine yapılandırma dosyasında veya uygulama yapılandırma dosyasında kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe26c-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="fe26c-134">**Allowlocation**</span><span class="sxs-lookup"><span data-stu-id="fe26c-134">**allowLocation**</span></span>   | <span data-ttu-id="fe26c-135">Bölümün \*\* \<konum>\*\* öğesi içinde kullanılıp kullanılamayacağı belirlenir.</span><span class="sxs-lookup"><span data-stu-id="fe26c-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="fe26c-136">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="fe26c-136">Use one of the following values:</span></span><br><br><span data-ttu-id="fe26c-137">**true**</span><span class="sxs-lookup"><span data-stu-id="fe26c-137">**true**</span></span><br><span data-ttu-id="fe26c-138">Bölümün \*\* \<konum>\*\* öğesi içinde kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe26c-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="fe26c-139">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="fe26c-139">This is the default.</span></span><br><span data-ttu-id="fe26c-140">**yanlış**</span><span class="sxs-lookup"><span data-stu-id="fe26c-140">**false**</span></span><br><span data-ttu-id="fe26c-141">Bölümün \*\* \<konum>\*\* öğesi içinde kullanılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="fe26c-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="fe26c-142">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="fe26c-142">Parent elements</span></span>

|     | <span data-ttu-id="fe26c-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe26c-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fe26c-144">\*\* \<configSections>\*\* Öğe</span><span class="sxs-lookup"><span data-stu-id="fe26c-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="fe26c-145">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe26c-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="fe26c-146">\*\* \<bölümGrup>\*\* Öğe</span><span class="sxs-lookup"><span data-stu-id="fe26c-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="fe26c-147">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe26c-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="fe26c-148">\*\* \<Bir bölüm>\*\* öğesi \*\* \<configSections>\*\* veya \*\* \<sectionGroup>\*\* bir alt öğesidir, ancak her ikisi de değil.</span><span class="sxs-lookup"><span data-stu-id="fe26c-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="fe26c-149">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fe26c-149">Child elements</span></span>

<span data-ttu-id="fe26c-150">None</span><span class="sxs-lookup"><span data-stu-id="fe26c-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="fe26c-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe26c-151">Remarks</span></span>

<span data-ttu-id="fe26c-152">Yapılandırma bölümü bildirmek, yapılandırma dosyası için temelde yeni bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe26c-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="fe26c-153">Yeni öğe, yapılandırma bölümü işleyicisinin (diğer bir şekilde <xref:System.Configuration.IConfigurationSectionHandler> arabirimi uygulayan bir sınıfın) okuduğu ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="fe26c-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="fe26c-154">Tanımladığınız bir bölümün öznitelikleri ve alt öğeleri, ayarlarınızı okumak için kullandığınız bölüm işleyicisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fe26c-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="fe26c-155">*Machine.config* dosyasında bir yapılandırma bölümü işleyicisi bildirmek, **allowDefinition** özniteliği aksini belirtmediği sürece, o bilgisayardaki herhangi bir uygulama yapılandırma dosyasında yapılandırma bölümünü kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe26c-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="fe26c-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe26c-156">Example</span></span>

<span data-ttu-id="fe26c-157">Aşağıdaki örnekte, yapılandırma bölümünün nasıl tanımlanılıgı ve bu bölümün ayarlarını nasıl tanımlanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fe26c-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler"
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="fe26c-158">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="fe26c-158">Configuration file</span></span>

<span data-ttu-id="fe26c-159">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe26c-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe26c-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe26c-160">See also</span></span>

- [<span data-ttu-id="fe26c-161">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="fe26c-161">Configuration file schema for the .NET Framework</span></span>](index.md)
