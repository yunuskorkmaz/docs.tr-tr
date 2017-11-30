---
title: "&lt;disableCommitThreadStack&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d74566b71501cf21081ac894048bb1c29e0ad94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdisablecommitthreadstackgt-element"></a><span data-ttu-id="b13b8-102">&lt;disableCommitThreadStack&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="b13b8-102">&lt;disableCommitThreadStack&gt; Element</span></span>
<span data-ttu-id="b13b8-103">Bir iş parçacığı başlatıldığında tam iş parçacığı yığın kaydedilmiş olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b13b8-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="b13b8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="b13b8-104">\<configuration></span></span>  
<span data-ttu-id="b13b8-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="b13b8-105">\<runtime></span></span>  
<span data-ttu-id="b13b8-106">\<disableCommitThreadStack ></span><span class="sxs-lookup"><span data-stu-id="b13b8-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b13b8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b13b8-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b13b8-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b13b8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b13b8-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b13b8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b13b8-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b13b8-110">Attributes</span></span>  
  
|<span data-ttu-id="b13b8-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b13b8-111">Attribute</span></span>|<span data-ttu-id="b13b8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b13b8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b13b8-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="b13b8-113">enabled</span></span>|<span data-ttu-id="b13b8-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b13b8-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b13b8-115">İş parçacığı başlangıç (varsayılan davranış) tam iş parçacığı yığında yürüten devre dışı olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b13b8-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b13b8-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b13b8-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="b13b8-117">Değer</span><span class="sxs-lookup"><span data-stu-id="b13b8-117">Value</span></span>|<span data-ttu-id="b13b8-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b13b8-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b13b8-119">0</span><span class="sxs-lookup"><span data-stu-id="b13b8-119">0</span></span>|<span data-ttu-id="b13b8-120">Ortak dil çalışma zamanı varsayılan davranışının bir iş parçacığı başlatıldığında tam iş parçacığı yığın tamamlamaya olduğu devre dışı bırakmayın.</span><span class="sxs-lookup"><span data-stu-id="b13b8-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="b13b8-121">1.</span><span class="sxs-lookup"><span data-stu-id="b13b8-121">1</span></span>|<span data-ttu-id="b13b8-122">Ortak dil çalışma zamanı varsayılan davranışının bir iş parçacığı başlatıldığında tam iş parçacığı yığın tamamlamaya olduğu devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="b13b8-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b13b8-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b13b8-123">Child Elements</span></span>  
 <span data-ttu-id="b13b8-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="b13b8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b13b8-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b13b8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b13b8-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="b13b8-126">Element</span></span>|<span data-ttu-id="b13b8-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b13b8-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b13b8-128">Ortak dil çalışma zamanı tarafından kullanılan her yapılandırma dosyası kök öğesinde ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="b13b8-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="b13b8-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="b13b8-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b13b8-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b13b8-130">Remarks</span></span>  
 <span data-ttu-id="b13b8-131">Ortak dil çalışma zamanı'nın varsayılan davranışını bir iş parçacığı başlatıldığında tam iş parçacığı yığın tamamlamaya ' dir.</span><span class="sxs-lookup"><span data-stu-id="b13b8-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="b13b8-132">Hemen bir iş parçacığı st olduğunda ortak dil çalışma zamanı tam iş parçacığı yığın yürütme değil, sunucunun çok sayıda iş parçacığı bellek sınırlı bir sunucuda oluşturulması gerekir ve bu iş parçacıklarının en çok az yığın alanı kullanır, daha iyi gerçekleştirebilir arted.</span><span class="sxs-lookup"><span data-stu-id="b13b8-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b13b8-133">Yönetilmeyen konakları kullanabileceğiniz `STARTUP_DISABLE_COMMITTHREADSTACK` başlangıç bayrağı [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) aynı sonucu gerçekleştirmek için numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="b13b8-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b13b8-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="b13b8-134">Example</span></span>  
 <span data-ttu-id="b13b8-135">Aşağıdaki örnek iş parçacığı başlangıç tam iş parçacığı yığında tamamlamaya olduğu ortak dil çalışma zamanı varsayılan davranışı devre dışı bırakma gösterir.</span><span class="sxs-lookup"><span data-stu-id="b13b8-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b13b8-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b13b8-136">See Also</span></span>  
 [<span data-ttu-id="b13b8-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b13b8-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="b13b8-138">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="b13b8-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
