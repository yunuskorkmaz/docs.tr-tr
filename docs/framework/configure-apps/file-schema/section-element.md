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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153742"
---
# <a name="section-element"></a><span data-ttu-id="202fd-102">\<section> öğesi</span><span class="sxs-lookup"><span data-stu-id="202fd-102">\<section> element</span></span>

<span data-ttu-id="202fd-103">Bir yapılandırma bölümü bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="202fd-103">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="202fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="202fd-104">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="202fd-105">Gerekli öznitelikler</span><span class="sxs-lookup"><span data-stu-id="202fd-105">Required attributes</span></span>

|           | <span data-ttu-id="202fd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="202fd-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="202fd-107">**ada**</span><span class="sxs-lookup"><span data-stu-id="202fd-107">**name**</span></span>  | <span data-ttu-id="202fd-108">Yapılandırma bölümünün adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="202fd-108">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="202fd-109">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="202fd-109">**type**</span></span>  | <span data-ttu-id="202fd-110">Yapılandırma dosyasından bölümü okuyan yapılandırma bölümü işleyici sınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="202fd-110">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="202fd-111">Tür değeri "tam nitelikli-bölüm-işleyici-sınıf-adı, basit-derleme-adı" sözdizimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="202fd-111">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="202fd-112">Basit derleme adı, *. dll* dosya uzantısı olmayan kök dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="202fd-112">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="202fd-113">İsteğe bağlı öznitelikler</span><span class="sxs-lookup"><span data-stu-id="202fd-113">Optional attributes</span></span>

<span data-ttu-id="202fd-114">Aşağıdaki öznitelikler yalnızca ASP.NET uygulamaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="202fd-114">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="202fd-115">Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="202fd-115">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="202fd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="202fd-116">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="202fd-117">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="202fd-117">**allowDefinition**</span></span> | <span data-ttu-id="202fd-118">Bölümün hangi yapılandırma dosyasına kullanılabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="202fd-118">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="202fd-119">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="202fd-119">Use one of the following values:</span></span><br><br><span data-ttu-id="202fd-120">**Yer**</span><span class="sxs-lookup"><span data-stu-id="202fd-120">**Everywhere**</span></span><br><span data-ttu-id="202fd-121">Bölümün herhangi bir yapılandırma dosyasında kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="202fd-121">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="202fd-122">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="202fd-122">This is the default.</span></span><br><span data-ttu-id="202fd-123">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="202fd-123">**MachineOnly**</span></span><br><span data-ttu-id="202fd-124">Bölümün yalnızca makine yapılandırma dosyasında (*Machine. config*) kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="202fd-124">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="202fd-125">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="202fd-125">**MachineToApplication**</span></span><br><span data-ttu-id="202fd-126">Bölümün makine yapılandırma dosyasında veya uygulama yapılandırma dosyasında kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="202fd-126">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="202fd-127">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="202fd-127">**allowLocation**</span></span>   | <span data-ttu-id="202fd-128">Bölümün öğe içinde kullanılıp kullanılamayacağını belirler **\<location>** .</span><span class="sxs-lookup"><span data-stu-id="202fd-128">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="202fd-129">Aşağıdaki değerlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="202fd-129">Use one of the following values:</span></span><br><br><span data-ttu-id="202fd-130">**değeri**</span><span class="sxs-lookup"><span data-stu-id="202fd-130">**true**</span></span><br><span data-ttu-id="202fd-131">Bölümünün öğesi içinde kullanılmasına izin verir **\<location>** .</span><span class="sxs-lookup"><span data-stu-id="202fd-131">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="202fd-132">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="202fd-132">This is the default.</span></span><br><span data-ttu-id="202fd-133">**yanlýþ**</span><span class="sxs-lookup"><span data-stu-id="202fd-133">**false**</span></span><br><span data-ttu-id="202fd-134">, Bölümün öğesi içinde kullanılmasına izin vermez **\<location>** .</span><span class="sxs-lookup"><span data-stu-id="202fd-134">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="202fd-135">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="202fd-135">Parent elements</span></span>

|     | <span data-ttu-id="202fd-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="202fd-136">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="202fd-137">**\<configSections>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="202fd-137">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="202fd-138">Yapılandırma bölümü ve ad alanı bildirimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="202fd-138">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="202fd-139">**\<sectionGroup>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="202fd-139">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="202fd-140">Yapılandırma bölümleri için bir ad alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="202fd-140">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="202fd-141">**\<section>** Öğesi, veya öğelerinin alt öğesidir **\<configSections>** **\<sectionGroup>** .</span><span class="sxs-lookup"><span data-stu-id="202fd-141">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="202fd-142">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="202fd-142">Child elements</span></span>

<span data-ttu-id="202fd-143">Yok</span><span class="sxs-lookup"><span data-stu-id="202fd-143">None</span></span>

## <a name="remarks"></a><span data-ttu-id="202fd-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="202fd-144">Remarks</span></span>

<span data-ttu-id="202fd-145">Bir yapılandırma bölümünün bildirilmesi, temel olarak yapılandırma dosyası için yeni bir öğe tanımlar.</span><span class="sxs-lookup"><span data-stu-id="202fd-145">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="202fd-146">Yeni öğe, bir yapılandırma bölümü işleyicisinin (yani, arabirimini uygulayan bir sınıf <xref:System.Configuration.IConfigurationSectionHandler> ) okuduğu ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="202fd-146">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="202fd-147">Tanımladığınız bir bölümün öznitelikleri ve alt öğeleri, ayarlarınızı okumak için kullandığınız bölüm işleyicisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="202fd-147">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="202fd-148">*Machine. config* dosyasında bir yapılandırma bölümü işleyicisi bildirmek, **allowDefinition** özniteliği aksini belirtmedikçe, bu bilgisayardaki herhangi bir uygulama yapılandırma dosyasında yapılandırma bölümünü kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="202fd-148">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="202fd-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="202fd-149">Example</span></span>

<span data-ttu-id="202fd-150">Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="202fd-150">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="202fd-151">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="202fd-151">Configuration file</span></span>

<span data-ttu-id="202fd-152">Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="202fd-152">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="202fd-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="202fd-153">See also</span></span>

- [<span data-ttu-id="202fd-154">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="202fd-154">Configuration file schema for the .NET Framework</span></span>](index.md)
