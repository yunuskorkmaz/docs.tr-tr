---
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
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921009"
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="4bafd-102">\<linkedConfiguration> öğesi</span><span class="sxs-lookup"><span data-stu-id="4bafd-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="4bafd-103">Dahil edilecek bir yapılandırma dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bafd-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="4bafd-104">[ **\<Yapılandırma >** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4bafd-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="4bafd-105">&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4bafd-105">&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="4bafd-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="4bafd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4bafd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bafd-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="4bafd-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4bafd-108">Attribute</span></span>

|           | <span data-ttu-id="4bafd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bafd-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4bafd-110">**değerini**</span><span class="sxs-lookup"><span data-stu-id="4bafd-110">**href**</span></span>  | <span data-ttu-id="4bafd-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4bafd-111">Required attribute.</span></span><br><br><span data-ttu-id="4bafd-112">Dahil edilecek yapılandırma dosyasının URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="4bafd-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="4bafd-113">**Href** özniteliği `file://`için desteklenen tek Biçim.</span><span class="sxs-lookup"><span data-stu-id="4bafd-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="4bafd-114">Yerel dosyalar ve UNC dosyaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4bafd-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4bafd-115">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="4bafd-115">Parent element</span></span>

|     | <span data-ttu-id="4bafd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bafd-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4bafd-117">assemblyBinding > öğesi  **\<** </span><span class="sxs-lookup"><span data-stu-id="4bafd-117">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="4bafd-118">Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bafd-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4bafd-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4bafd-119">Child elements</span></span>

<span data-ttu-id="4bafd-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="4bafd-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4bafd-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bafd-121">Remarks</span></span>

<span data-ttu-id="4bafd-122">**\<LinkedConfiguration>** öğesi bileşeni derlemeler için bakım basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="4bafd-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="4bafd-123">İyi bilinen bir konumda bulunan bir yapılandırma dosyası bir derleme bir veya daha fazla kullanmanız durumunda derleme kullanan uygulamaların yapılandırma dosyalarını kullanabilirler **\<linkedConfiguration>** yapılandırma bilgilerini doğrudan dahil olmak üzere yerine derleme yapılandırma dosyası eklenecek öğe.</span><span class="sxs-lookup"><span data-stu-id="4bafd-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="4bafd-124">Bileşen derlemesine hizmet verilirken, ortak yapılandırma dosyasını güncelleştirme, derlemeyi kullanan tüm uygulamalara güncelleştirilmiş yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bafd-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="4bafd-125">**\<LinkedConfiguration>** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4bafd-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="4bafd-126">Aşağıdaki kurallar, bağlantılı yapılandırma dosyalarının kullanımını yönetir:</span><span class="sxs-lookup"><span data-stu-id="4bafd-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="4bafd-127">Dahil edilen yapılandırma dosyalarındaki ayarlar yalnızca yükleyici bağlama ilkesini etkiler ve yalnızca yükleyici tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4bafd-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="4bafd-128">Dahil edilen yapılandırma dosyaları, bağlama ilkeleri dışında ayarları olabilir, ancak bu ayarların hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4bafd-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="4bafd-129">`href`Özniteliğiiçin desteklenen tek Biçim. `file://`</span><span class="sxs-lookup"><span data-stu-id="4bafd-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="4bafd-130">Yerel dosyalar ve UNC dosyaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4bafd-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="4bafd-131">Yapılandırma dosyası başına bağlı yapılandırma sayısında kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="4bafd-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="4bafd-132">Tüm bağlantılı yapılandırma dosyaları, C/ `#include` C++içindeki yönergesinin davranışına benzer şekilde tek bir dosya oluşturacak şekilde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4bafd-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="4bafd-133">**\<LinkedConfiguration>** öğesi yalnızca uygulama yapılandırma dosyalarında izin verilir; içindeki sayılır *Machine.config*.</span><span class="sxs-lookup"><span data-stu-id="4bafd-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="4bafd-134">Döngüsel başvurular algılanır ve sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4bafd-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="4bafd-135">Diğer bir deyişle, **\<linkedConfiguration>** yapılandırma dosyalarını bir dizi öğeleri formunda bir döngü, döngü algılandı ve durduruldu.</span><span class="sxs-lookup"><span data-stu-id="4bafd-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="4bafd-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bafd-136">Example</span></span>

<span data-ttu-id="4bafd-137">Aşağıdaki örnek, yerel sabit diskten yapılandırma dosyasının nasıl ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="4bafd-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4bafd-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bafd-138">See also</span></span>

- [<span data-ttu-id="4bafd-139">assemblyBinding > öğesi  **\<** </span><span class="sxs-lookup"><span data-stu-id="4bafd-139">**\<assemblyBinding>** Element</span></span>](assemblybinding-element-for-configuration.md)
- [<span data-ttu-id="4bafd-140">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="4bafd-140">Configuration file schema for the .NET Framework</span></span>](index.md)
