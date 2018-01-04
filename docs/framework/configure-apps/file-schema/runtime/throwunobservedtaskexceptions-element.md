---
title: "&lt;ThrowUnobservedTaskExceptions&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 635270a6461b573663b7719843d81ff2b23e63dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a><span data-ttu-id="14b2b-102">&lt;ThrowUnobservedTaskExceptions&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="14b2b-102">&lt;ThrowUnobservedTaskExceptions&gt; Element</span></span>
<span data-ttu-id="14b2b-103">İşlenmemiş görev özel durumlarını çalışan bir işlemi sonlandırmak olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="14b2b-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="14b2b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="14b2b-104">\<configuration></span></span>  
<span data-ttu-id="14b2b-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="14b2b-105">\<runtime></span></span>  
<span data-ttu-id="14b2b-106">\<ThrowUnobservedTaskExceptions ></span><span class="sxs-lookup"><span data-stu-id="14b2b-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14b2b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14b2b-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14b2b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="14b2b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="14b2b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="14b2b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14b2b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="14b2b-110">Attributes</span></span>  
  
|<span data-ttu-id="14b2b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="14b2b-111">Attribute</span></span>|<span data-ttu-id="14b2b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14b2b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="14b2b-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="14b2b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="14b2b-114">İşlenmemiş görev özel durumlarını çalışan işlemi sonlanmalıdır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="14b2b-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="14b2b-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="14b2b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="14b2b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="14b2b-116">Value</span></span>|<span data-ttu-id="14b2b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14b2b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="14b2b-118">Bir görev işlenmeyen özel durum için çalışan işlemi sonlandırmak değil.</span><span class="sxs-lookup"><span data-stu-id="14b2b-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="14b2b-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="14b2b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="14b2b-120">Bir görev işlenmeyen özel durum için çalışan işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="14b2b-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14b2b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="14b2b-121">Child Elements</span></span>  
 <span data-ttu-id="14b2b-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="14b2b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14b2b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="14b2b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="14b2b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="14b2b-124">Element</span></span>|<span data-ttu-id="14b2b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14b2b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="14b2b-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="14b2b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="14b2b-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="14b2b-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="14b2b-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14b2b-128">Remarks</span></span>  
 <span data-ttu-id="14b2b-129">İle ilişkili bir özel durum, bir <xref:System.Threading.Tasks.Task> olmayan gözlenir, var. hiçbir <xref:System.Threading.Tasks.Task.Wait%2A> işlemi, üst iliştirilmemiş ve <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği, görev özel durum olarak kabul unobserved olması değil okundu.</span><span class="sxs-lookup"><span data-stu-id="14b2b-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="14b2b-130">İçinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], göre varsayılan bir <xref:System.Threading.Tasks.Task> bir unobserved olan özel durum çöp toplama, sonlandırıcıyı bir özel durum oluşturur ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="14b2b-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="14b2b-131">İşlem sonlandırma çöp toplama ve sonlandırma zamanlama tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="14b2b-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="14b2b-132">Geliştiriciler görevlerini temel alan zaman uyumsuz kod yazmayı kolaylaştırmak için [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] unobserved özel durumlar için bu varsayılan davranışı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="14b2b-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="14b2b-133">Özel durumlar hala neden unobserved <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> oluşturulması için olay ancak varsayılan olarak, işlem değil sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="14b2b-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="14b2b-134">Bunun yerine, bir olay işleyicisi özel gözlemleyen bağımsız olarak olay tetiklenir sonra özel durum göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="14b2b-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="14b2b-135">İçinde [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], kullanabileceğiniz [ \<ThrowUnobservedTaskExceptions > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) etkinleştirmek için bir uygulama yapılandırma dosyasında [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] bir özel durum atma davranışı.</span><span class="sxs-lookup"><span data-stu-id="14b2b-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="14b2b-136">Ayrıca aşağıdaki yollardan biriyle özel durum davranışını belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="14b2b-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="14b2b-137">Ortam değişkenini ayarlayarak `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="14b2b-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="14b2b-138">DWORD kayıt defteri ayarı ThrowUnobservedTaskExceptions değer = 1 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="14b2b-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14b2b-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="14b2b-139">Example</span></span>  
 <span data-ttu-id="14b2b-140">Aşağıdaki örnek, görevleri özel durumları atma uygulama yapılandırma dosyası kullanarak etkinleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="14b2b-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="14b2b-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="14b2b-141">Example</span></span>  
 <span data-ttu-id="14b2b-142">Aşağıdaki örnek, bir unobserved özel bir görevden nasıl durum gösterir.</span><span class="sxs-lookup"><span data-stu-id="14b2b-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="14b2b-143">Kod düzgün çalışması için yayımlanan bir program olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14b2b-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="14b2b-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14b2b-144">See Also</span></span>  
 [<span data-ttu-id="14b2b-145">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="14b2b-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="14b2b-146">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="14b2b-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
