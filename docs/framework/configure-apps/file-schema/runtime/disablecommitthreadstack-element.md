---
description: 'Daha fazla bilgi edinin: <disableCommitThreadStack> öğesi'
title: <disableCommitThreadStack> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
ms.openlocfilehash: f80a23b12f67b9f3df1ddb010edb735225f6f7a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787103"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="54060-103">\<disableCommitThreadStack> Öğesi</span><span class="sxs-lookup"><span data-stu-id="54060-103">\<disableCommitThreadStack> Element</span></span>

<span data-ttu-id="54060-104">Bir iş parçacığı başlatıldığında tam iş parçacığı yığınının uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54060-104">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="54060-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="54060-105">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54060-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="54060-106">Attributes and Elements</span></span>  

 <span data-ttu-id="54060-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54060-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54060-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="54060-108">Attributes</span></span>  
  
|<span data-ttu-id="54060-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="54060-109">Attribute</span></span>|<span data-ttu-id="54060-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54060-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54060-111">enabled</span><span class="sxs-lookup"><span data-stu-id="54060-111">enabled</span></span>|<span data-ttu-id="54060-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="54060-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="54060-113">Tüm iş parçacığı yığınının iş parçacığı başlangıcında (varsayılan davranış) devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54060-113">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="54060-114">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="54060-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="54060-115">Değer</span><span class="sxs-lookup"><span data-stu-id="54060-115">Value</span></span>|<span data-ttu-id="54060-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54060-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54060-117">0</span><span class="sxs-lookup"><span data-stu-id="54060-117">0</span></span>|<span data-ttu-id="54060-118">Ortak dil çalışma zamanının varsayılan davranışını devre dışı bırakmayın, bu, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54060-118">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="54060-119">1</span><span class="sxs-lookup"><span data-stu-id="54060-119">1</span></span>|<span data-ttu-id="54060-120">Ortak dil çalışma zamanının varsayılan davranışını devre dışı bırakın, bu, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54060-120">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54060-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="54060-121">Child Elements</span></span>  

 <span data-ttu-id="54060-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="54060-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54060-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="54060-123">Parent Elements</span></span>  
  
|<span data-ttu-id="54060-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="54060-124">Element</span></span>|<span data-ttu-id="54060-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54060-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="54060-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="54060-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="54060-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="54060-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54060-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54060-128">Remarks</span></span>  

 <span data-ttu-id="54060-129">Ortak dil çalışma zamanının varsayılan davranışı, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmeniz olur.</span><span class="sxs-lookup"><span data-stu-id="54060-129">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="54060-130">Sınırlı belleği olan bir sunucuda çok sayıda iş parçacığı oluşturulması gerekiyorsa ve bu iş parçacıklarının çoğu çok az yığın alanı kullanıyorsa, ortak dil çalışma zamanı, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını hemen yürütmezse sunucu daha iyi çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="54060-130">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54060-131">Yönetilmeyen konaklar, `STARTUP_DISABLE_COMMITTHREADSTACK` [startup_flags](../../../unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırmasında başlangıç bayrağını kullanarak aynı sonucu elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="54060-131">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54060-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="54060-132">Example</span></span>  

 <span data-ttu-id="54060-133">Aşağıdaki örnek, ortak dil çalışma zamanının varsayılan davranışının devre dışı bırakılacağını gösterir. Bu, iş parçacığı başlangıcında tam iş parçacığı yığınını yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54060-133">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54060-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54060-134">See also</span></span>

- [<span data-ttu-id="54060-135">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="54060-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="54060-136">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="54060-136">Configuration File Schema</span></span>](../index.md)
