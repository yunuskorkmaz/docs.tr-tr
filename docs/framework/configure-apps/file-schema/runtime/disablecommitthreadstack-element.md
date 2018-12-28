---
title: '&lt;disableCommitThreadStack&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69b2c9f3bbd4fb7562272903d3ab78e3a4312298
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611652"
---
# <a name="ltdisablecommitthreadstackgt-element"></a><span data-ttu-id="e5b76-102">&lt;disableCommitThreadStack&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="e5b76-102">&lt;disableCommitThreadStack&gt; Element</span></span>
<span data-ttu-id="e5b76-103">Bir iş parçacığı başlatıldığında iş parçacığı yığınının tamamının taahhüt olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5b76-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="e5b76-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e5b76-104">\<configuration></span></span>  
<span data-ttu-id="e5b76-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="e5b76-105">\<runtime></span></span>  
<span data-ttu-id="e5b76-106">\<disableCommitThreadStack ></span><span class="sxs-lookup"><span data-stu-id="e5b76-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b76-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5b76-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5b76-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5b76-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e5b76-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5b76-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5b76-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5b76-110">Attributes</span></span>  
  
|<span data-ttu-id="e5b76-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e5b76-111">Attribute</span></span>|<span data-ttu-id="e5b76-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5b76-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5b76-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="e5b76-113">enabled</span></span>|<span data-ttu-id="e5b76-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e5b76-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e5b76-115">İş parçacığı başlangıç (varsayılan davranış) üzerinde tam iş parçacığı yığın Yürütülüyor etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5b76-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e5b76-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e5b76-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="e5b76-117">Değer</span><span class="sxs-lookup"><span data-stu-id="e5b76-117">Value</span></span>|<span data-ttu-id="e5b76-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5b76-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e5b76-119">0</span><span class="sxs-lookup"><span data-stu-id="e5b76-119">0</span></span>|<span data-ttu-id="e5b76-120">Ortak dil çalışma zamanı'nın varsayılan davranışını bir iş parçacığı başlatıldığında tam iş parçacığı yığını tamamlamaya olduğu devre dışı bırakmayın.</span><span class="sxs-lookup"><span data-stu-id="e5b76-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="e5b76-121">1.</span><span class="sxs-lookup"><span data-stu-id="e5b76-121">1</span></span>|<span data-ttu-id="e5b76-122">İş parçacığı yığınının tamamının bir iş parçacığı başlatıldığında işleme olan ortak dil çalışma zamanı'nın varsayılan davranışını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="e5b76-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5b76-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5b76-123">Child Elements</span></span>  
 <span data-ttu-id="e5b76-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5b76-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5b76-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5b76-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e5b76-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5b76-126">Element</span></span>|<span data-ttu-id="e5b76-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5b76-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e5b76-128">Her yapılandırma dosyasında ortak dil çalışma zamanı tarafından kullanılan kök öğe ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="e5b76-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="e5b76-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e5b76-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5b76-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5b76-130">Remarks</span></span>  
 <span data-ttu-id="e5b76-131">Ortak dil çalışma zamanı'nın varsayılan davranışını bir iş parçacığı başlatıldığında iş parçacığı yığınının tamamının işleme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="e5b76-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="e5b76-132">Hemen bir iş parçacığı st olduğunda ortak dil çalışma zamanı iş parçacığı yığınının tamamının kaydetmeyen bir işlevi, sunucu çok sayıda iş parçacığı belleğin sınırlı olduğu bir sunucuda oluşturulması gerekir ve bu iş parçacıklarının en çok az yığın alanı kullanır, daha iyi gerçekleştirebilir başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="e5b76-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5b76-133">Yönetilmeyen konak kullanabilir `STARTUP_DISABLE_COMMITTHREADSTACK` başlangıç bayrağı [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) aynı sonuca ulaşmak için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e5b76-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5b76-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5b76-134">Example</span></span>  
 <span data-ttu-id="e5b76-135">Aşağıdaki örnek, iş parçacığı yığınının tamamının iş parçacığı başlangıç işleme olan ortak dil çalışma zamanı'nın varsayılan davranışını devre dışı bırakmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5b76-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5b76-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5b76-136">See Also</span></span>  
- [<span data-ttu-id="e5b76-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e5b76-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="e5b76-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e5b76-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
