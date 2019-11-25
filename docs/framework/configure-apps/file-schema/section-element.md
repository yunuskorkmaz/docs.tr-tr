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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c1675540df6844f98572c11cfb140bff23b31a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089028"
---
# <a name="section-element"></a><span data-ttu-id="28cbf-102">\<Bölüm > öğesi</span><span class="sxs-lookup"><span data-stu-id="28cbf-102">\<section> element</span></span>

<span data-ttu-id="28cbf-103">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="28cbf-104">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="28cbf-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="28cbf-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="28cbf-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="28cbf-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<bölüm >**</span><span class="sxs-lookup"><span data-stu-id="28cbf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="28cbf-107">[ **\<configuration >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="28cbf-107">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="28cbf-108">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="28cbf-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="28cbf-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup >** ](sectiongroup-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="28cbf-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>\
<span data-ttu-id="28cbf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bölümü >**</span><span class="sxs-lookup"><span data-stu-id="28cbf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="28cbf-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28cbf-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="28cbf-112">Gerekli öznitelikler</span><span class="sxs-lookup"><span data-stu-id="28cbf-112">Required attributes</span></span>

|           | <span data-ttu-id="28cbf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28cbf-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="28cbf-114">**ada**</span><span class="sxs-lookup"><span data-stu-id="28cbf-114">**name**</span></span>  | <span data-ttu-id="28cbf-115">Yapılandırma bölümünün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="28cbf-116">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="28cbf-116">**type**</span></span>  | <span data-ttu-id="28cbf-117">Yapılandırma dosyasından bölümü okuyan yapılandırma bölümü işleyici sınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="28cbf-118">Tür değeri "tam nitelikli-bölüm-işleyici-sınıf-adı, basit-derleme-adı" sözdizimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="28cbf-119">Basit derleme adı, *. dll* dosya uzantısı olmayan kök dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="28cbf-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="28cbf-120">İsteğe bağlı öznitelikler</span><span class="sxs-lookup"><span data-stu-id="28cbf-120">Optional attributes</span></span>

<span data-ttu-id="28cbf-121">Aşağıdaki öznitelikler yalnızca ASP.NET uygulamaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="28cbf-122">Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="28cbf-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="28cbf-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28cbf-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="28cbf-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="28cbf-124">**allowDefinition**</span></span> | <span data-ttu-id="28cbf-125">Bölümün hangi yapılandırma dosyasına kullanılabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="28cbf-126">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="28cbf-126">Use one of the following values:</span></span><br><br><span data-ttu-id="28cbf-127">**Yer**</span><span class="sxs-lookup"><span data-stu-id="28cbf-127">**Everywhere**</span></span><br><span data-ttu-id="28cbf-128">Bölümün herhangi bir yapılandırma dosyasında kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="28cbf-129">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="28cbf-129">This is the default.</span></span><br><span data-ttu-id="28cbf-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="28cbf-130">**MachineOnly**</span></span><br><span data-ttu-id="28cbf-131">Bölümün yalnızca makine yapılandırma dosyasında (*Machine. config*) kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="28cbf-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="28cbf-132">**MachineToApplication**</span></span><br><span data-ttu-id="28cbf-133">Bölümün makine yapılandırma dosyasında veya uygulama yapılandırma dosyasında kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="28cbf-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="28cbf-134">**allowLocation**</span></span>   | <span data-ttu-id="28cbf-135">Bölümün **\<location >** öğesi içinde kullanılıp kullanılamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="28cbf-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="28cbf-136">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="28cbf-136">Use one of the following values:</span></span><br><br><span data-ttu-id="28cbf-137">**true**</span><span class="sxs-lookup"><span data-stu-id="28cbf-137">**true**</span></span><br><span data-ttu-id="28cbf-138">Bölümün **\<location >** öğesi içinde kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="28cbf-139">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="28cbf-139">This is the default.</span></span><br><span data-ttu-id="28cbf-140">**false**</span><span class="sxs-lookup"><span data-stu-id="28cbf-140">**false**</span></span><br><span data-ttu-id="28cbf-141">Bölümün **\<location >** öğesi içinde kullanılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="28cbf-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="28cbf-142">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="28cbf-142">Parent elements</span></span>

|     | <span data-ttu-id="28cbf-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28cbf-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="28cbf-144"> **\<configSections >** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="28cbf-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="28cbf-145">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="28cbf-146"> **\<sectionGroup >** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="28cbf-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="28cbf-147">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="28cbf-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="28cbf-148">**\<bölüm >** öğesi, **\<configSections >** veya **\<sectionGroup >** alt öğesidir, ancak her ikisine birden değil.</span><span class="sxs-lookup"><span data-stu-id="28cbf-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="28cbf-149">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="28cbf-149">Child elements</span></span>

<span data-ttu-id="28cbf-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="28cbf-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="28cbf-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28cbf-151">Remarks</span></span>

<span data-ttu-id="28cbf-152">Bir yapılandırma bölümünün bildirilmesi, temel olarak yapılandırma dosyası için yeni bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="28cbf-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="28cbf-153">Yeni öğe, bir yapılandırma bölümü işleyicisinin (yani, <xref:System.Configuration.IConfigurationSectionHandler> arabirimini uygulayan bir sınıf) okuduğu ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="28cbf-154">Tanımladığınız bir bölümün öznitelikleri ve alt öğeleri, ayarlarınızı okumak için kullandığınız bölüm işleyicisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="28cbf-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="28cbf-155">*Machine. config* dosyasında bir yapılandırma bölümü işleyicisi bildirmek, **allowDefinition** özniteliği aksini belirtmedikçe, bu bilgisayardaki herhangi bir uygulama yapılandırma dosyasında yapılandırma bölümünü kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="28cbf-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="28cbf-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="28cbf-156">Example</span></span>

<span data-ttu-id="28cbf-157">Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="28cbf-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="28cbf-158">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="28cbf-158">Configuration file</span></span>

<span data-ttu-id="28cbf-159">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="28cbf-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="28cbf-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28cbf-160">See also</span></span>

- [<span data-ttu-id="28cbf-161">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="28cbf-161">Configuration file schema for the .NET Framework</span></span>](index.md)
