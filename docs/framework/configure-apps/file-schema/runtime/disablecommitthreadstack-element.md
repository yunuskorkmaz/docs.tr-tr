---
title: <disableCommitThreadStack> Öğesi
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
ms.openlocfilehash: 08ffd6ffcb9a8fa356d486f6d2ae1113de0fa682
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674226"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="1f126-102">\<disableCommitThreadStack > öğesi</span><span class="sxs-lookup"><span data-stu-id="1f126-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="1f126-103">Bir iş parçacığı başlatıldığında iş parçacığı yığınının tamamının taahhüt olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f126-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="1f126-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="1f126-104">\<configuration></span></span>  
<span data-ttu-id="1f126-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="1f126-105">\<runtime></span></span>  
<span data-ttu-id="1f126-106">\<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="1f126-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f126-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f126-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f126-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f126-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1f126-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f126-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f126-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1f126-110">Attributes</span></span>  
  
|<span data-ttu-id="1f126-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1f126-111">Attribute</span></span>|<span data-ttu-id="1f126-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f126-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f126-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="1f126-113">enabled</span></span>|<span data-ttu-id="1f126-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1f126-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="1f126-115">İş parçacığı başlangıç (varsayılan davranış) üzerinde tam iş parçacığı yığın Yürütülüyor etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f126-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1f126-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1f126-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="1f126-117">Değer</span><span class="sxs-lookup"><span data-stu-id="1f126-117">Value</span></span>|<span data-ttu-id="1f126-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f126-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f126-119">0</span><span class="sxs-lookup"><span data-stu-id="1f126-119">0</span></span>|<span data-ttu-id="1f126-120">Ortak dil çalışma zamanı'nın varsayılan davranışını bir iş parçacığı başlatıldığında tam iş parçacığı yığını tamamlamaya olduğu devre dışı bırakmayın.</span><span class="sxs-lookup"><span data-stu-id="1f126-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="1f126-121">1.</span><span class="sxs-lookup"><span data-stu-id="1f126-121">1</span></span>|<span data-ttu-id="1f126-122">İş parçacığı yığınının tamamının bir iş parçacığı başlatıldığında işleme olan ortak dil çalışma zamanı'nın varsayılan davranışını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="1f126-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f126-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f126-123">Child Elements</span></span>  
 <span data-ttu-id="1f126-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="1f126-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f126-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1f126-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1f126-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="1f126-126">Element</span></span>|<span data-ttu-id="1f126-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f126-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1f126-128">Her yapılandırma dosyasında ortak dil çalışma zamanı tarafından kullanılan kök öğe ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="1f126-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="1f126-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1f126-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f126-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f126-130">Remarks</span></span>  
 <span data-ttu-id="1f126-131">Ortak dil çalışma zamanı'nın varsayılan davranışını bir iş parçacığı başlatıldığında iş parçacığı yığınının tamamının işleme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1f126-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="1f126-132">Hemen bir iş parçacığı st olduğunda ortak dil çalışma zamanı iş parçacığı yığınının tamamının kaydetmeyen bir işlevi, sunucu çok sayıda iş parçacığı belleğin sınırlı olduğu bir sunucuda oluşturulması gerekir ve bu iş parçacıklarının en çok az yığın alanı kullanır, daha iyi gerçekleştirebilir başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="1f126-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f126-133">Yönetilmeyen konak kullanabilir `STARTUP_DISABLE_COMMITTHREADSTACK` başlangıç bayrağı [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) aynı sonuca ulaşmak için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1f126-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f126-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f126-134">Example</span></span>  
 <span data-ttu-id="1f126-135">Aşağıdaki örnek, iş parçacığı yığınının tamamının iş parçacığı başlangıç işleme olan ortak dil çalışma zamanı'nın varsayılan davranışını devre dışı bırakmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f126-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f126-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f126-136">See also</span></span>

- [<span data-ttu-id="1f126-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1f126-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="1f126-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="1f126-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
