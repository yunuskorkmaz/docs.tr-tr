---
title: <developmentMode> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117627"
---
# <a name="developmentmode-element"></a><span data-ttu-id="fc3ca-102">\<developmentMode> Öğesi</span><span class="sxs-lookup"><span data-stu-id="fc3ca-102">\<developmentMode> Element</span></span>
<span data-ttu-id="fc3ca-103">Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="fc3ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc3ca-104">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc3ca-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc3ca-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fc3ca-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc3ca-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fc3ca-107">Attributes</span></span>  
  
|<span data-ttu-id="fc3ca-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fc3ca-108">Attribute</span></span>|<span data-ttu-id="fc3ca-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc3ca-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc3ca-110">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="fc3ca-110">**developerInstallation**</span></span>|<span data-ttu-id="fc3ca-111">Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-111">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="fc3ca-112">developerInstallation özniteliği</span><span class="sxs-lookup"><span data-stu-id="fc3ca-112">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="fc3ca-113">Değer</span><span class="sxs-lookup"><span data-stu-id="fc3ca-113">Value</span></span>|<span data-ttu-id="fc3ca-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc3ca-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fc3ca-115">**değeri**</span><span class="sxs-lookup"><span data-stu-id="fc3ca-115">**true**</span></span>|<span data-ttu-id="fc3ca-116">DEVPATH ortam değişkeni tarafından belirtilen dizinlerdeki derlemeleri arar.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-116">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="fc3ca-117">**yanlýþ**</span><span class="sxs-lookup"><span data-stu-id="fc3ca-117">**false**</span></span>|<span data-ttu-id="fc3ca-118">, DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramaz.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-118">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="fc3ca-119">Bu, varsayılan</span><span class="sxs-lookup"><span data-stu-id="fc3ca-119">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc3ca-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc3ca-120">Child Elements</span></span>  
 <span data-ttu-id="fc3ca-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc3ca-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc3ca-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fc3ca-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="fc3ca-123">Element</span></span>|<span data-ttu-id="fc3ca-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc3ca-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fc3ca-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fc3ca-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc3ca-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc3ca-127">Remarks</span></span>  
 <span data-ttu-id="fc3ca-128">Bu ayarı yalnızca geliştirme zamanında kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-128">Use this setting only at development time.</span></span> <span data-ttu-id="fc3ca-129">Çalışma zamanı, DEVPATH 'de bulunan kesin adlı derlemelerin sürümlerini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-129">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="fc3ca-130">Yalnızca bulduğu ilk derlemeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-130">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc3ca-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc3ca-131">Example</span></span>  
 <span data-ttu-id="fc3ca-132">Aşağıdaki örnek, çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeler aramasına neden olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-132">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc3ca-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc3ca-133">See also</span></span>

- [<span data-ttu-id="fc3ca-134">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="fc3ca-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fc3ca-135">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="fc3ca-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fc3ca-136">Nasıl yapılır: DEVPATH Kullanarak Derlemelerin Konumunu Bulma</span><span class="sxs-lookup"><span data-stu-id="fc3ca-136">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
