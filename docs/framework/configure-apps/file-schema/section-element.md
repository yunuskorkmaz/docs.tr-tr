---
title: '&lt;bölüm&gt; öğesi'
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
ms.openlocfilehash: 17b44ca93efc26f4732f5fe2926f894257d8f984
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746442"
---
# <a name="section-element"></a><span data-ttu-id="aac9a-102">\<Bölüm > öğesi</span><span class="sxs-lookup"><span data-stu-id="aac9a-102">\<section> element</span></span>

<span data-ttu-id="aac9a-103">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="aac9a-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="aac9a-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aac9a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="aac9a-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="aac9a-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="aac9a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="aac9a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="aac9a-107">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aac9a-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="aac9a-108">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="aac9a-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="aac9a-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="aac9a-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="aac9a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="aac9a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="aac9a-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aac9a-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="aac9a-112">Gerekli öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aac9a-112">Required attributes</span></span>

|           | <span data-ttu-id="aac9a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aac9a-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="aac9a-114">**Adı**</span><span class="sxs-lookup"><span data-stu-id="aac9a-114">**name**</span></span>  | <span data-ttu-id="aac9a-115">Yapılandırma bölümünün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aac9a-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="aac9a-116">**Türü**</span><span class="sxs-lookup"><span data-stu-id="aac9a-116">**type**</span></span>  | <span data-ttu-id="aac9a-117">Yapılandırma dosyasından bölüm okur yapılandırma bölümü işleyici sınıf adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aac9a-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="aac9a-118">Tür değeri "fully-qualified-section-handler-class-name, basit derleme adı" sözdizimine sahip.</span><span class="sxs-lookup"><span data-stu-id="aac9a-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="aac9a-119">Kök filename olmadan basit derleme adı: *.dll* dosya uzantısı.</span><span class="sxs-lookup"><span data-stu-id="aac9a-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="aac9a-120">İsteğe bağlı öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="aac9a-120">Optional attributes</span></span>

<span data-ttu-id="aac9a-121">Aşağıdaki öznitelikler, yalnızca ASP.NET uygulamaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aac9a-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="aac9a-122">Yapılandırma sistemi diğer uygulama türleri için bu öznitelikler yoksayar.</span><span class="sxs-lookup"><span data-stu-id="aac9a-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="aac9a-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aac9a-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="aac9a-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="aac9a-124">**allowDefinition**</span></span> | <span data-ttu-id="aac9a-125">Bölüm kullanılabilir hangi yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aac9a-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="aac9a-126">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="aac9a-126">Use one of the following values:</span></span><br><br><span data-ttu-id="aac9a-127">**Her yerde**</span><span class="sxs-lookup"><span data-stu-id="aac9a-127">**Everywhere**</span></span><br><span data-ttu-id="aac9a-128">Her yapılandırma dosyasında kullanılacak bölümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="aac9a-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="aac9a-129">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="aac9a-129">This is the default.</span></span><br><span data-ttu-id="aac9a-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="aac9a-130">**MachineOnly**</span></span><br><span data-ttu-id="aac9a-131">Yalnızca makine yapılandırma dosyasında kullanılacak bölümü sağlar (*Machine.config*).</span><span class="sxs-lookup"><span data-stu-id="aac9a-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="aac9a-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="aac9a-132">**MachineToApplication**</span></span><br><span data-ttu-id="aac9a-133">Makine yapılandırma dosyası veya uygulama yapılandırma dosyasında kullanılacak bölümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="aac9a-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="aac9a-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="aac9a-134">**allowLocation**</span></span>   | <span data-ttu-id="aac9a-135">Bölüm içinde kullanılıp kullanılamayacağını belirler  **\<konumu >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="aac9a-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="aac9a-136">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="aac9a-136">Use one of the following values:</span></span><br><br><span data-ttu-id="aac9a-137">**true**</span><span class="sxs-lookup"><span data-stu-id="aac9a-137">**true**</span></span><br><span data-ttu-id="aac9a-138">İçinde kullanılacak bölümü sağlar  **\<konumu >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="aac9a-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="aac9a-139">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="aac9a-139">This is the default.</span></span><br><span data-ttu-id="aac9a-140">**false**</span><span class="sxs-lookup"><span data-stu-id="aac9a-140">**false**</span></span><br><span data-ttu-id="aac9a-141">İçinde kullanılacak bölümüne izin vermiyor  **\<konumu >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="aac9a-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="aac9a-142">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="aac9a-142">Parent elements</span></span>

|     | <span data-ttu-id="aac9a-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aac9a-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="aac9a-144">**\<configSections >** öğesi</span><span class="sxs-lookup"><span data-stu-id="aac9a-144">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="aac9a-145">Yapılandırma bölümü ve ad alanı bildirimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="aac9a-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="aac9a-146">**\<sectionGroup >** öğesi</span><span class="sxs-lookup"><span data-stu-id="aac9a-146">**\<sectionGroup>** Element</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="aac9a-147">Yapılandırma bölümleri için bir ad alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aac9a-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="aac9a-148">A  **\<bölüm >** öğesi bir alt öğedir ya da  **\<configSections >** veya  **\<sectionGroup >** değil her ikisi de.</span><span class="sxs-lookup"><span data-stu-id="aac9a-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="aac9a-149">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="aac9a-149">Child elements</span></span>

<span data-ttu-id="aac9a-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="aac9a-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="aac9a-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aac9a-151">Remarks</span></span>

<span data-ttu-id="aac9a-152">Yapılandırma bölümü temelde bildirme yapılandırma dosyası için yeni bir öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aac9a-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="aac9a-153">Yeni öğe bir yapılandırma işleyici bölüm ayarları içerir (diğer bir deyişle, uygulayan bir sınıf <xref:System.Configuration.IConfigurationSectionHandler> arabirimi) okur.</span><span class="sxs-lookup"><span data-stu-id="aac9a-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="aac9a-154">Öznitelikler ve alt öğeler tanımladığınız bir bölümün ayarlarınızı okumak için kullandığınız bölüm işleyicisi bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="aac9a-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="aac9a-155">Yapılandırma bölümü işleyici bildirme *Machine.config* dosyası sağlar, bu bilgisayarda, tüm uygulama yapılandırma dosyasındaki yapılandırma bölümü kullanmanızı, sürece **allowDefinition**özniteliği belirtir. Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="aac9a-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="aac9a-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="aac9a-156">Example</span></span>

<span data-ttu-id="aac9a-157">Aşağıdaki örnek, bir yapılandırma bölümü ve o bölümün ayarlarının tanımlamaya gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="aac9a-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="aac9a-158">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="aac9a-158">Configuration file</span></span>

<span data-ttu-id="aac9a-159">Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.</span><span class="sxs-lookup"><span data-stu-id="aac9a-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="aac9a-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aac9a-160">See also</span></span>

[<span data-ttu-id="aac9a-161">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="aac9a-161">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
