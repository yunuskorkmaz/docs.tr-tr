---
title: "&lt;linkedConfiguration&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bfea438ec19303c35ad9d7a2816cb7b9473a00c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linkedconfiguration-element"></a><span data-ttu-id="e301d-102">\<linkedConfiguration > öğesi</span><span class="sxs-lookup"><span data-stu-id="e301d-102">\<linkedConfiguration> element</span></span>

<span data-ttu-id="e301d-103">Dahil etmek için bir yapılandırma dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="e301d-103">Specifies a configuration file to include.</span></span>

<span data-ttu-id="e301d-104">[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e301d-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="e301d-105">&nbsp;&nbsp;[**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e301d-105">&nbsp;&nbsp;[**\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
<span data-ttu-id="e301d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="e301d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e301d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e301d-107">Syntax</span></span>

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a><span data-ttu-id="e301d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e301d-108">Attribute</span></span>

|           | <span data-ttu-id="e301d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e301d-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="e301d-110">**href**</span><span class="sxs-lookup"><span data-stu-id="e301d-110">**href**</span></span>  | <span data-ttu-id="e301d-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e301d-111">Required attribute.</span></span><br><br><span data-ttu-id="e301d-112">Dahil etmek için yapılandırma dosyası URL'si.</span><span class="sxs-lookup"><span data-stu-id="e301d-112">The URL of the configuration file to include.</span></span> <span data-ttu-id="e301d-113">İçin desteklenen tek biçimi **href** özniteliği `file://`.</span><span class="sxs-lookup"><span data-stu-id="e301d-113">The only format supported for the **href** attribute is `file://`.</span></span> <span data-ttu-id="e301d-114">Yerel dosyaları ve UNC dosyaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e301d-114">Local files and UNC files are supported.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="e301d-115">Üst öğesi</span><span class="sxs-lookup"><span data-stu-id="e301d-115">Parent element</span></span>

|     | <span data-ttu-id="e301d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e301d-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e301d-117">**\<assemblyBinding >** öğesi</span><span class="sxs-lookup"><span data-stu-id="e301d-117">**\<assemblyBinding>** Element</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="e301d-118">Derleme bağlama ilkesi yapılandırma düzeyinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="e301d-118">Specifies assembly binding policy at the configuration level.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e301d-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e301d-119">Child elements</span></span>

<span data-ttu-id="e301d-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="e301d-120">None</span></span>

## <a name="remarks"></a><span data-ttu-id="e301d-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e301d-121">Remarks</span></span>

<span data-ttu-id="e301d-122">**\<LinkedConfiguration >** öğesi basitleştirir bileşen derlemeleri için bakım.</span><span class="sxs-lookup"><span data-stu-id="e301d-122">The **\<linkedConfiguration>** element simplifies servicing for component assemblies.</span></span> <span data-ttu-id="e301d-123">Bir veya daha fazla uygulama iyi bilinen bir konumda bulunan bir yapılandırma dosyası sahip bir derleme kullanıyorsanız, derleme kullanan uygulamalar, yapılandırma dosyalarını kullanabilirsiniz  **\<linkedConfiguration >** yapılandırma bilgilerini doğrudan da dahil olmak üzere yerine derleme yapılandırma dosyası eklenecek öğe.</span><span class="sxs-lookup"><span data-stu-id="e301d-123">If one or more applications use an assembly that has a configuration file residing in a well-known location, the configuration files of the applications that use the assembly can use the **\<linkedConfiguration>** element to include the assembly configuration file, rather than including configuration information directly.</span></span> <span data-ttu-id="e301d-124">Bileşen derleme hizmet, ortak yapılandırma dosyasını güncelleştirme derleme kullanan tüm uygulamalar için güncelleştirilmiş yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e301d-124">When the component assembly is serviced, updating the common configuration file provides updated configuration information to all applications that use the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="e301d-125">**\<LinkedConfiguration >** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e301d-125">The **\<linkedConfiguration>** element is not supported for applications with Windows side-by-side manifests.</span></span>

<span data-ttu-id="e301d-126">Aşağıdaki kuralları bağlantılı yapılandırma dosyaları kullanımını yöneten:</span><span class="sxs-lookup"><span data-stu-id="e301d-126">The following rules govern the use of linked configuration files:</span></span>

- <span data-ttu-id="e301d-127">Dahil edilen yapılandırma dosyalarında ayarlar yalnızca yükleyicisi bağlama ilkesi etkileyebilir ve yalnızca yükleyicisi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e301d-127">The settings in included configuration files only affect loader binding policy and are used only by the loader.</span></span> <span data-ttu-id="e301d-128">Dahil edilen yapılandırma dosyalarını ilkeleri bağlama farklı ayarlara sahip olabilir, ancak bu ayarları herhangi bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e301d-128">The included configuration files can have settings other than binding policies, but those settings don't have any effect.</span></span>

- <span data-ttu-id="e301d-129">İçin desteklenen tek biçimi `href` özniteliği `file://`.</span><span class="sxs-lookup"><span data-stu-id="e301d-129">The only format supported for the `href` attribute is `file://`.</span></span> <span data-ttu-id="e301d-130">Yerel dosyaları ve UNC dosyaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e301d-130">Local files and UNC files are supported.</span></span>

- <span data-ttu-id="e301d-131">Yapılandırma dosya başına bağlı yapılandırmalar sayısı hiçbir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="e301d-131">There is no constraint on the number of linked configurations per configuration file.</span></span>

- <span data-ttu-id="e301d-132">Tüm bağlantılı yapılandırma dosyaları için davranışını benzer bir dosyayı oluşturmak için birleştirilir `#include` C/c++ yönergesi.</span><span class="sxs-lookup"><span data-stu-id="e301d-132">All linked configuration files are merged to form one file, similar to the behavior of the `#include` directive in C/C++.</span></span>

- <span data-ttu-id="e301d-133">**\<LinkedConfiguration >** yalnızca uygulama yapılandırma dosyaları öğesine izin verilir; içinde göz ardı *Machine.config*.</span><span class="sxs-lookup"><span data-stu-id="e301d-133">The **\<linkedConfiguration>** element is allowed only in application configuration files; it's ignored in *Machine.config*.</span></span>

- <span data-ttu-id="e301d-134">Döngüsel başvuru algılandı ve sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="e301d-134">Circular references are detected and terminated.</span></span> <span data-ttu-id="e301d-135">Diğer bir deyişle,  **\<linkedConfiguration >** yapılandırma dosyalarını bir dizi öğeleri formunda bir döngü, döngü algılandı ve durduruldu.</span><span class="sxs-lookup"><span data-stu-id="e301d-135">That is, if the **\<linkedConfiguration>** elements of a series of configuration files form a loop, the loop is detected and stopped.</span></span>

## <a name="example"></a><span data-ttu-id="e301d-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="e301d-136">Example</span></span>

<span data-ttu-id="e301d-137">Aşağıdaki örnek, yerel sabit disk yapılandırma dosyasından dahil gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e301d-137">The following example shows how to include configuration file from the local hard disk:</span></span>

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e301d-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e301d-138">See also</span></span>

<span data-ttu-id="e301d-139">[**\<assemblyBinding >** öğesi](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e301d-139">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) </span></span>  
[<span data-ttu-id="e301d-140">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e301d-140">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
