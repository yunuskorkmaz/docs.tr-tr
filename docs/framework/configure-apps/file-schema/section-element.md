---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <section> öğesi'
title: <section> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 7756f7ee3be2391a0d068708f3719083640b5595
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639945"
---
# <a name="section-element"></a><span data-ttu-id="57675-104">\<section> öğesi</span><span class="sxs-lookup"><span data-stu-id="57675-104">\<section> element</span></span>

<span data-ttu-id="57675-105">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="57675-105">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="57675-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="57675-106">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="57675-107">Gerekli öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57675-107">Required attributes</span></span>

|           | <span data-ttu-id="57675-108">Description</span><span class="sxs-lookup"><span data-stu-id="57675-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="57675-109">**ada**</span><span class="sxs-lookup"><span data-stu-id="57675-109">**name**</span></span>  | <span data-ttu-id="57675-110">Yapılandırma bölümünün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="57675-110">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="57675-111">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="57675-111">**type**</span></span>  | <span data-ttu-id="57675-112">Yapılandırma dosyasından bölümü okuyan yapılandırma bölümü işleyici sınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="57675-112">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="57675-113">Tür değeri "tam nitelikli-bölüm-işleyici-sınıf-adı, basit-derleme-adı" sözdizimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="57675-113">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="57675-114">Basit derleme adı, *. dll* dosya uzantısı olmayan kök dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="57675-114">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="57675-115">İsteğe bağlı öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57675-115">Optional attributes</span></span>

<span data-ttu-id="57675-116">Aşağıdaki öznitelikler yalnızca ASP.NET uygulamaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57675-116">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="57675-117">Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="57675-117">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="57675-118">Description</span><span class="sxs-lookup"><span data-stu-id="57675-118">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="57675-119">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="57675-119">**allowDefinition**</span></span> | <span data-ttu-id="57675-120">Bölümün hangi yapılandırma dosyasına kullanılabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57675-120">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="57675-121">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="57675-121">Use one of the following values:</span></span><br><br><span data-ttu-id="57675-122">**Yer**</span><span class="sxs-lookup"><span data-stu-id="57675-122">**Everywhere**</span></span><br><span data-ttu-id="57675-123">Bölümün herhangi bir yapılandırma dosyasında kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="57675-123">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="57675-124">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="57675-124">This is the default.</span></span><br><span data-ttu-id="57675-125">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="57675-125">**MachineOnly**</span></span><br><span data-ttu-id="57675-126">Bölümün yalnızca makine yapılandırma dosyasında (*Machine.config*) kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="57675-126">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="57675-127">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="57675-127">**MachineToApplication**</span></span><br><span data-ttu-id="57675-128">Bölümün makine yapılandırma dosyasında veya uygulama yapılandırma dosyasında kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="57675-128">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="57675-129">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="57675-129">**allowLocation**</span></span>   | <span data-ttu-id="57675-130">Bölümün öğe içinde kullanılıp kullanılamayacağını belirler **\<location>** .</span><span class="sxs-lookup"><span data-stu-id="57675-130">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="57675-131">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="57675-131">Use one of the following values:</span></span><br><br><span data-ttu-id="57675-132">**değeri**</span><span class="sxs-lookup"><span data-stu-id="57675-132">**true**</span></span><br><span data-ttu-id="57675-133">Bölümünün öğesi içinde kullanılmasına izin verir **\<location>** .</span><span class="sxs-lookup"><span data-stu-id="57675-133">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="57675-134">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="57675-134">This is the default.</span></span><br><span data-ttu-id="57675-135">**yanlýþ**</span><span class="sxs-lookup"><span data-stu-id="57675-135">**false**</span></span><br><span data-ttu-id="57675-136">, Bölümün öğesi içinde kullanılmasına izin vermez **\<location>** .</span><span class="sxs-lookup"><span data-stu-id="57675-136">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="57675-137">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="57675-137">Parent elements</span></span>

|     | <span data-ttu-id="57675-138">Description</span><span class="sxs-lookup"><span data-stu-id="57675-138">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="57675-139">**\<configSections>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="57675-139">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="57675-140">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="57675-140">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="57675-141">**\<sectionGroup>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="57675-141">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="57675-142">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="57675-142">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="57675-143">**\<section>** Öğesi, veya öğelerinin alt öğesidir **\<configSections>** **\<sectionGroup>** .</span><span class="sxs-lookup"><span data-stu-id="57675-143">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="57675-144">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="57675-144">Child elements</span></span>

<span data-ttu-id="57675-145">Yok</span><span class="sxs-lookup"><span data-stu-id="57675-145">None</span></span>

## <a name="remarks"></a><span data-ttu-id="57675-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57675-146">Remarks</span></span>

<span data-ttu-id="57675-147">Bir yapılandırma bölümünün bildirilmesi, temel olarak yapılandırma dosyası için yeni bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="57675-147">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="57675-148">Yeni öğe, bir yapılandırma bölümü işleyicisinin (yani, arabirimini uygulayan bir sınıf <xref:System.Configuration.IConfigurationSectionHandler> ) okuduğu ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="57675-148">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="57675-149">Tanımladığınız bir bölümün öznitelikleri ve alt öğeleri, ayarlarınızı okumak için kullandığınız bölüm işleyicisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="57675-149">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="57675-150">*Machine.config* dosyasında bir yapılandırma bölümü işleyicisi bildirmek, **allowDefinition** özniteliği aksini belirtmedikçe, bu bilgisayardaki herhangi bir uygulama yapılandırma dosyasında yapılandırma bölümünü kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="57675-150">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="57675-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="57675-151">Example</span></span>

<span data-ttu-id="57675-152">Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="57675-152">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="57675-153">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="57675-153">Configuration file</span></span>

<span data-ttu-id="57675-154">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57675-154">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="57675-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57675-155">See also</span></span>

- [<span data-ttu-id="57675-156">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="57675-156">Configuration file schema for the .NET Framework</span></span>](index.md)
