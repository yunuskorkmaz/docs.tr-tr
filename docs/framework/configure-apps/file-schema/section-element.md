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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 94f7709f4bd273515d9fcdd727354ec579c46207
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927222"
---
# <a name="section-element"></a><span data-ttu-id="f004e-102">\<Bölüm > öğesi</span><span class="sxs-lookup"><span data-stu-id="f004e-102">\<section> element</span></span>

<span data-ttu-id="f004e-103">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="f004e-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="f004e-104">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f004e-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="f004e-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f004e-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f004e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="f004e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="f004e-107">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f004e-107">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="f004e-108">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f004e-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f004e-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup >** ](sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="f004e-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="f004e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Bölüm >**</span><span class="sxs-lookup"><span data-stu-id="f004e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f004e-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f004e-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="f004e-112">Gerekli öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f004e-112">Required attributes</span></span>

|           | <span data-ttu-id="f004e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f004e-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f004e-114">**name**</span><span class="sxs-lookup"><span data-stu-id="f004e-114">**name**</span></span>  | <span data-ttu-id="f004e-115">Yapılandırma bölümünün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f004e-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="f004e-116">**type**</span><span class="sxs-lookup"><span data-stu-id="f004e-116">**type**</span></span>  | <span data-ttu-id="f004e-117">Yapılandırma dosyasından bölümü okuyan yapılandırma bölümü işleyici sınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f004e-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="f004e-118">Tür değeri "tam nitelikli-bölüm-işleyici-sınıf-adı, basit-derleme-adı" sözdizimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f004e-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="f004e-119">Basit derleme adı, *. dll* dosya uzantısı olmayan kök dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="f004e-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="f004e-120">İsteğe bağlı öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f004e-120">Optional attributes</span></span>

<span data-ttu-id="f004e-121">Aşağıdaki öznitelikler yalnızca ASP.NET uygulamaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f004e-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="f004e-122">Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="f004e-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="f004e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f004e-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="f004e-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="f004e-124">**allowDefinition**</span></span> | <span data-ttu-id="f004e-125">Bölümün hangi yapılandırma dosyasına kullanılabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f004e-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="f004e-126">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="f004e-126">Use one of the following values:</span></span><br><br><span data-ttu-id="f004e-127">**Yer**</span><span class="sxs-lookup"><span data-stu-id="f004e-127">**Everywhere**</span></span><br><span data-ttu-id="f004e-128">Bölümün herhangi bir yapılandırma dosyasında kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f004e-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="f004e-129">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="f004e-129">This is the default.</span></span><br><span data-ttu-id="f004e-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="f004e-130">**MachineOnly**</span></span><br><span data-ttu-id="f004e-131">Bölümün yalnızca makine yapılandırma dosyasında (*Machine. config*) kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f004e-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="f004e-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="f004e-132">**MachineToApplication**</span></span><br><span data-ttu-id="f004e-133">Bölümün makine yapılandırma dosyasında veya uygulama yapılandırma dosyasında kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f004e-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="f004e-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="f004e-134">**allowLocation**</span></span>   | <span data-ttu-id="f004e-135">Bölümün  **\<location >** öğesi içinde kullanılıp kullanılamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="f004e-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="f004e-136">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="f004e-136">Use one of the following values:</span></span><br><br><span data-ttu-id="f004e-137">**true**</span><span class="sxs-lookup"><span data-stu-id="f004e-137">**true**</span></span><br><span data-ttu-id="f004e-138">Bölümün  **\<location >** öğesi içinde kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f004e-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="f004e-139">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="f004e-139">This is the default.</span></span><br><span data-ttu-id="f004e-140">**false**</span><span class="sxs-lookup"><span data-stu-id="f004e-140">**false**</span></span><br><span data-ttu-id="f004e-141">, Bölümün  **\<location >** öğesi içinde kullanılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f004e-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="f004e-142">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f004e-142">Parent elements</span></span>

|     | <span data-ttu-id="f004e-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f004e-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f004e-144"> **configSections>\<** öğesi</span><span class="sxs-lookup"><span data-stu-id="f004e-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="f004e-145">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f004e-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="f004e-146"> **sectionGroup>\<** öğesi</span><span class="sxs-lookup"><span data-stu-id="f004e-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="f004e-147">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f004e-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="f004e-148">**Bir\<Bölüm >** öğesi,  **\<configSections >** veya  **\<sectionGroup >** alt öğesidir ancak her ikisine birden değil.</span><span class="sxs-lookup"><span data-stu-id="f004e-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="f004e-149">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f004e-149">Child elements</span></span>

<span data-ttu-id="f004e-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="f004e-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="f004e-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f004e-151">Remarks</span></span>

<span data-ttu-id="f004e-152">Bir yapılandırma bölümünün bildirilmesi, temel olarak yapılandırma dosyası için yeni bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f004e-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="f004e-153">Yeni öğe, bir yapılandırma bölümü işleyicisinin (yani, <xref:System.Configuration.IConfigurationSectionHandler> arabirimini uygulayan bir sınıf) okuduğu ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="f004e-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="f004e-154">Tanımladığınız bir bölümün öznitelikleri ve alt öğeleri, ayarlarınızı okumak için kullandığınız bölüm işleyicisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f004e-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="f004e-155">*Machine. config* dosyasında bir yapılandırma bölümü işleyicisi bildirmek, **allowDefinition** özniteliği aksini belirtmedikçe, bu bilgisayardaki herhangi bir uygulama yapılandırma dosyasında yapılandırma bölümünü kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f004e-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="f004e-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="f004e-156">Example</span></span>

<span data-ttu-id="f004e-157">Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f004e-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="f004e-158">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="f004e-158">Configuration file</span></span>

<span data-ttu-id="f004e-159">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f004e-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f004e-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f004e-160">See also</span></span>

- [<span data-ttu-id="f004e-161">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="f004e-161">Configuration file schema for the .NET Framework</span></span>](index.md)
