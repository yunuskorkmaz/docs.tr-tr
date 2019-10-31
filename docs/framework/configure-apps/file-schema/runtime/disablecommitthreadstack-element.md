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
ms.openlocfilehash: 8aefb8a20d6a95c5b8062d0c03dcb28a3557ca3d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117468"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="67b49-102">\<disableCommitThreadStack > öğesi</span><span class="sxs-lookup"><span data-stu-id="67b49-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="67b49-103">Bir iş parçacığı başlatıldığında tam iş parçacığı yığınının uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="67b49-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
<span data-ttu-id="67b49-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="67b49-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="67b49-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="67b49-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="67b49-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack >**</span><span class="sxs-lookup"><span data-stu-id="67b49-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b49-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67b49-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67b49-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="67b49-108">Attributes and Elements</span></span>  
 <span data-ttu-id="67b49-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="67b49-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67b49-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="67b49-110">Attributes</span></span>  
  
|<span data-ttu-id="67b49-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="67b49-111">Attribute</span></span>|<span data-ttu-id="67b49-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67b49-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67b49-113">etkinletir</span><span class="sxs-lookup"><span data-stu-id="67b49-113">enabled</span></span>|<span data-ttu-id="67b49-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="67b49-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="67b49-115">Tüm iş parçacığı yığınının iş parçacığı başlangıcında (varsayılan davranış) devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="67b49-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="67b49-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="67b49-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="67b49-117">Değer</span><span class="sxs-lookup"><span data-stu-id="67b49-117">Value</span></span>|<span data-ttu-id="67b49-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67b49-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="67b49-119">0</span><span class="sxs-lookup"><span data-stu-id="67b49-119">0</span></span>|<span data-ttu-id="67b49-120">Ortak dil çalışma zamanının varsayılan davranışını devre dışı bırakmayın, bu, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67b49-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="67b49-121">1\.</span><span class="sxs-lookup"><span data-stu-id="67b49-121">1</span></span>|<span data-ttu-id="67b49-122">Ortak dil çalışma zamanının varsayılan davranışını devre dışı bırakın, bu, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67b49-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67b49-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="67b49-123">Child Elements</span></span>  
 <span data-ttu-id="67b49-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="67b49-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67b49-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="67b49-125">Parent Elements</span></span>  
  
|<span data-ttu-id="67b49-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="67b49-126">Element</span></span>|<span data-ttu-id="67b49-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67b49-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="67b49-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="67b49-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="67b49-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="67b49-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67b49-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67b49-130">Remarks</span></span>  
 <span data-ttu-id="67b49-131">Ortak dil çalışma zamanının varsayılan davranışı, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmeniz olur.</span><span class="sxs-lookup"><span data-stu-id="67b49-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="67b49-132">Sınırlı belleği olan bir sunucuda çok sayıda iş parçacığı oluşturulması gerekiyorsa ve bu iş parçacıklarının çoğu çok az yığın alanı kullanıyorsa, ortak dil çalışma zamanı, iş parçacığı St olduğunda tam iş parçacığı yığınını hemen yürütmezse sunucu daha iyi çalışabilir. başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="67b49-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67b49-133">Yönetilmeyen konaklar, [startup_flags](../../../unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırmasında `STARTUP_DISABLE_COMMITTHREADSTACK` başlangıç bayrağını kullanarak aynı sonucu elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="67b49-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67b49-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="67b49-134">Example</span></span>  
 <span data-ttu-id="67b49-135">Aşağıdaki örnek, ortak dil çalışma zamanının varsayılan davranışının devre dışı bırakılacağını gösterir. Bu, iş parçacığı başlangıcında tam iş parçacığı yığınını yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="67b49-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="67b49-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67b49-136">See also</span></span>

- [<span data-ttu-id="67b49-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="67b49-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="67b49-138">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="67b49-138">Configuration File Schema</span></span>](../index.md)
