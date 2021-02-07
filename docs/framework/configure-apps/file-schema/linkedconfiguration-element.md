---
description: 'Daha fazla bilgi edinin: <linkedConfiguration> öğesi'
title: <linkedConfiguration> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: e4312cf788784241efc35304b632dfe1fdef1bc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698667"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="0d002-103">\<linkedConfiguration> öğesi</span><span class="sxs-lookup"><span data-stu-id="0d002-103">\<linkedConfiguration> element</span></span>

<span data-ttu-id="0d002-104">Dahil edilecek bir yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d002-104">Specifies a configuration file to include.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a><span data-ttu-id="0d002-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d002-105">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="0d002-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0d002-106">Attribute</span></span>

|           | <span data-ttu-id="0d002-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d002-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="0d002-108">**değerini**</span><span class="sxs-lookup"><span data-stu-id="0d002-108">**href**</span></span>  | <span data-ttu-id="0d002-109">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0d002-109">Required attribute.</span></span><br><br><span data-ttu-id="0d002-110">Dahil edilecek yapılandırma dosyasının URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="0d002-110">The URL of the configuration file to include.</span></span> <span data-ttu-id="0d002-111">**Href** özniteliği için desteklenen tek Biçim `file://` .</span><span class="sxs-lookup"><span data-stu-id="0d002-111">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="0d002-112">Yerel dosyalar ve UNC dosyaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0d002-112">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="0d002-113">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="0d002-113">Parent element</span></span>

|     | <span data-ttu-id="0d002-114">Description</span><span class="sxs-lookup"><span data-stu-id="0d002-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0d002-115">**\<assemblyBinding>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="0d002-115">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="0d002-116">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d002-116">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0d002-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0d002-117">Child elements</span></span>

<span data-ttu-id="0d002-118">Yok</span><span class="sxs-lookup"><span data-stu-id="0d002-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="0d002-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d002-119">Remarks</span></span>

<span data-ttu-id="0d002-120">**\<linkedConfiguration>** Öğesi bileşen derlemelerinin bakımını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d002-120">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="0d002-121">Bir veya daha fazla uygulama, iyi bilinen bir konumda bulunan bir yapılandırma dosyası olan bir derlemeyi kullanıyorsa, derlemeyi kullanan uygulamaların yapılandırma dosyaları, **\<linkedConfiguration>** yapılandırma bilgilerini doğrudan eklemek yerine, derleme yapılandırma dosyasını dahil etmek için öğesini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0d002-121">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="0d002-122">Bileşen derlemesine hizmet verilirken, ortak yapılandırma dosyasını güncelleştirme, derlemeyi kullanan tüm uygulamalara güncelleştirilmiş yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d002-122">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="0d002-123">**\<linkedConfiguration>** Windows yan yana bildirimleri olan uygulamalar için öğesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0d002-123">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="0d002-124">Aşağıdaki kurallar, bağlantılı yapılandırma dosyalarının kullanımını yönetir:</span><span class="sxs-lookup"><span data-stu-id="0d002-124">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="0d002-125">Dahil edilen yapılandırma dosyalarındaki ayarlar yalnızca yükleyici bağlama ilkesini etkiler ve yalnızca yükleyici tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d002-125">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="0d002-126">Dahil edilen yapılandırma dosyaları, bağlama ilkeleri dışında ayarları olabilir, ancak bu ayarların hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0d002-126">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="0d002-127">Özniteliği için desteklenen tek Biçim `href` `file://` .</span><span class="sxs-lookup"><span data-stu-id="0d002-127">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="0d002-128">Yerel dosyalar ve UNC dosyaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0d002-128">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="0d002-129">Yapılandırma dosyası başına bağlı yapılandırma sayısında kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="0d002-129">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="0d002-130">Tüm bağlantılı yapılandırma dosyaları, `#include` C/C++ içindeki yönergedeki davranışa benzer şekilde tek bir dosya oluşturacak şekilde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0d002-130">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="0d002-131">**\<linkedConfiguration>** Öğesine yalnızca uygulama yapılandırma dosyalarında izin verilir; *Machine.config* yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="0d002-131">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="0d002-132">Döngüsel başvurular algılanır ve sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0d002-132">Circular references are detected and terminated.</span></span> <span data-ttu-id="0d002-133">Diğer bir deyişle, **\<linkedConfiguration>** bir dizi yapılandırma dosyası öğesi bir döngü oluşturuyor ise döngü algılanır ve durdurulur.</span><span class="sxs-lookup"><span data-stu-id="0d002-133">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="0d002-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d002-134">Example</span></span>

<span data-ttu-id="0d002-135">Aşağıdaki örnek, yerel sabit diskten yapılandırma dosyasının nasıl ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="0d002-135">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0d002-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d002-136">See also</span></span>

- [<span data-ttu-id="0d002-137">**\<assemblyBinding>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="0d002-137">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="0d002-138">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="0d002-138">Configuration file schema for the .NET Framework</span></span>](index.md)
