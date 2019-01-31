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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 58f823ce0c128f30e361b4a631d41286533b5f0f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259221"
---
# <a name="section-element"></a><span data-ttu-id="53865-102">\<Bölüm > öğesi</span><span class="sxs-lookup"><span data-stu-id="53865-102">\<section> element</span></span>

<span data-ttu-id="53865-103">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="53865-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="53865-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="53865-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="53865-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="53865-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="53865-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="53865-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="53865-107">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="53865-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="53865-108">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="53865-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="53865-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="53865-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="53865-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="53865-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="53865-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53865-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="53865-112">Gerekli öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="53865-112">Required attributes</span></span>

|           | <span data-ttu-id="53865-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53865-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="53865-114">**Adı**</span><span class="sxs-lookup"><span data-stu-id="53865-114">**name**</span></span>  | <span data-ttu-id="53865-115">Yapılandırma bölümünün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53865-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="53865-116">**type**</span><span class="sxs-lookup"><span data-stu-id="53865-116">**type**</span></span>  | <span data-ttu-id="53865-117">Bölüm yapılandırma dosyasından okur yapılandırma bölümü işleyici sınıf adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53865-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="53865-118">Türü değeri "fully-qualified-section-handler-class-name, basit bütünleştirilmiş kod adı" sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="53865-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="53865-119">Kök dosya adı olmadan basit derleme adı: *.dll* dosya uzantısı.</span><span class="sxs-lookup"><span data-stu-id="53865-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="53865-120">İsteğe bağlı öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="53865-120">Optional attributes</span></span>

<span data-ttu-id="53865-121">Aşağıdaki öznitelikleri, yalnızca ASP.NET uygulamaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="53865-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="53865-122">Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikler yok sayar.</span><span class="sxs-lookup"><span data-stu-id="53865-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="53865-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53865-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="53865-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="53865-124">**allowDefinition**</span></span> | <span data-ttu-id="53865-125">Bölüm kullanılabilir hangi yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53865-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="53865-126">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="53865-126">Use one of the following values:</span></span><br><br><span data-ttu-id="53865-127">**Her yerde**</span><span class="sxs-lookup"><span data-stu-id="53865-127">**Everywhere**</span></span><br><span data-ttu-id="53865-128">Herhangi bir yapılandırma dosyasında kullanılacak bölüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="53865-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="53865-129">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="53865-129">This is the default.</span></span><br><span data-ttu-id="53865-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="53865-130">**MachineOnly**</span></span><br><span data-ttu-id="53865-131">Yalnızca makine yapılandırma dosyasında kullanılacak bölüm sağlar (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="53865-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="53865-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="53865-132">**MachineToApplication**</span></span><br><span data-ttu-id="53865-133">Makine yapılandırma dosyası veya uygulama yapılandırma dosyasında kullanılacak bölüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="53865-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="53865-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="53865-134">**allowLocation**</span></span>   | <span data-ttu-id="53865-135">Bölüm içinde kullanılmasına izin verilip verilmeyeceğini belirler  **\<konum >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="53865-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="53865-136">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="53865-136">Use one of the following values:</span></span><br><br><span data-ttu-id="53865-137">**true**</span><span class="sxs-lookup"><span data-stu-id="53865-137">**true**</span></span><br><span data-ttu-id="53865-138">İçinde kullanılacak bölüm tanır  **\<konum >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="53865-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="53865-139">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="53865-139">This is the default.</span></span><br><span data-ttu-id="53865-140">**false**</span><span class="sxs-lookup"><span data-stu-id="53865-140">**false**</span></span><br><span data-ttu-id="53865-141">İçinde kullanılacak bölümüne izin vermiyor  **\<konum >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="53865-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="53865-142">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="53865-142">Parent elements</span></span>

|     | <span data-ttu-id="53865-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53865-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="53865-144">**\<configSections >** öğesi</span><span class="sxs-lookup"><span data-stu-id="53865-144">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="53865-145">Yapılandırma bölümü ve ad alanı bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="53865-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="53865-146">**\<sectionGroup >** öğesi</span><span class="sxs-lookup"><span data-stu-id="53865-146">**\<sectionGroup>** Element</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="53865-147">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="53865-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="53865-148">A  **\<bölüm >** öğedir ya da alt öğesi  **\<configSections >** veya  **\<sectionGroup >** değil her ikisi de.</span><span class="sxs-lookup"><span data-stu-id="53865-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="53865-149">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="53865-149">Child elements</span></span>

<span data-ttu-id="53865-150">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="53865-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="53865-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53865-151">Remarks</span></span>

<span data-ttu-id="53865-152">Bir yapılandırma bölümünü temelde bildirme yapılandırma dosyası için yeni bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="53865-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="53865-153">Yeni bir öğe bir yapılandırma işleyici bölüm ayarları içerir (diğer bir deyişle, uygulayan bir sınıf <xref:System.Configuration.IConfigurationSectionHandler> arabirimi) okur.</span><span class="sxs-lookup"><span data-stu-id="53865-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="53865-154">Öznitelikler ve alt öğeleri tanımladığınız bir bölümün ayarlarınızı okumak için kullandığınız bölümü işleyicisinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="53865-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="53865-155">Bir yapılandırma bölümü işleyicisinde bildirme *Machine.config* dosya yapılandırma bölümü bu bilgisayarda, bir uygulama yapılandırma dosyasında kullanmanıza olanak sağlar sürece **allowDefinition**özniteliği, aksi takdirde belirtir.</span><span class="sxs-lookup"><span data-stu-id="53865-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="53865-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="53865-156">Example</span></span>

<span data-ttu-id="53865-157">Aşağıdaki örnek, bir yapılandırma bölümü tanımlayın ve bu bölümün ayarlarını tanımlamak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="53865-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="53865-158">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="53865-158">Configuration file</span></span>

<span data-ttu-id="53865-159">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="53865-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="53865-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53865-160">See also</span></span>

- [<span data-ttu-id="53865-161">.NET Framework yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="53865-161">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
