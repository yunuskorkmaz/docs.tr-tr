---
title: '&lt;ThrowUnobservedTaskExceptions&gt; öğesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cd3a7a4305dc60beb73b20580049e40780f95c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515660"
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a><span data-ttu-id="55ce0-102">&lt;ThrowUnobservedTaskExceptions&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="55ce0-102">&lt;ThrowUnobservedTaskExceptions&gt; Element</span></span>
<span data-ttu-id="55ce0-103">Çalışan bir işleme, işlenmemiş bir görev özel durumlarını sonlandırma olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55ce0-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="55ce0-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="55ce0-104">\<configuration></span></span>  
<span data-ttu-id="55ce0-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="55ce0-105">\<runtime></span></span>  
<span data-ttu-id="55ce0-106">\<ThrowUnobservedTaskExceptions ></span><span class="sxs-lookup"><span data-stu-id="55ce0-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55ce0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55ce0-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55ce0-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55ce0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="55ce0-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55ce0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55ce0-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55ce0-110">Attributes</span></span>  
  
|<span data-ttu-id="55ce0-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55ce0-111">Attribute</span></span>|<span data-ttu-id="55ce0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55ce0-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="55ce0-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="55ce0-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="55ce0-114">İşlenmemiş bir görev özel durumlarını çalışan işlemi sonlandırması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="55ce0-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="55ce0-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55ce0-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="55ce0-116">Değer</span><span class="sxs-lookup"><span data-stu-id="55ce0-116">Value</span></span>|<span data-ttu-id="55ce0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55ce0-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="55ce0-118">İşlenmemiş bir görev özel durum için çalışan işlemi sonlandırmak değil.</span><span class="sxs-lookup"><span data-stu-id="55ce0-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="55ce0-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="55ce0-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="55ce0-120">İşlenmemiş bir görev özel durum için çalışan işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="55ce0-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55ce0-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55ce0-121">Child Elements</span></span>  
 <span data-ttu-id="55ce0-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="55ce0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55ce0-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55ce0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="55ce0-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="55ce0-124">Element</span></span>|<span data-ttu-id="55ce0-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55ce0-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55ce0-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="55ce0-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="55ce0-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="55ce0-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="55ce0-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55ce0-128">Remarks</span></span>  
 <span data-ttu-id="55ce0-129">İle ilişkili bir özel durum, bir <xref:System.Threading.Tasks.Task> gözlenmezse, orada hiçbir <xref:System.Threading.Tasks.Task.Wait%2A> işlemi, üst iliştirilmemiş ve <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği olmayan salt okunur görev özel durum gözetimsiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="55ce0-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="55ce0-130">İçinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]tarafından varsayılan bir <xref:System.Threading.Tasks.Task> gözetimsiz bir olan özel durum çöp olarak toplanacak, sonlandırıcı bir özel durum oluşturur ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="55ce0-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="55ce0-131">İşlemin sonlandırılmasına atık toplama ve sonlandırma zamanlaması tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="55ce0-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="55ce0-132">Geliştiriciler görevlerini temel alan zaman uyumsuz kod yazmayı kolaylaştırmak için [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] gözetimsiz özel durumlar için bu varsayılan davranışı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="55ce0-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="55ce0-133">Gözlemlenmeyen özel durumlar hala neden <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> oluşturulması için olay ancak varsayılan olarak, işlem değil sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="55ce0-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="55ce0-134">Bunun yerine, özel durum gözlemler bağımsız olarak bir olay işleyicisi, olay tetiklenir sonra özel durum yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="55ce0-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="55ce0-135">İçinde [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], kullanabileceğiniz [ \<ThrowUnobservedTaskExceptions > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) etkinleştirmek için bir uygulama yapılandırma dosyasında [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] bir özel durum davranış.</span><span class="sxs-lookup"><span data-stu-id="55ce0-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="55ce0-136">Özel durum davranışını aşağıdaki yollardan birini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="55ce0-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="55ce0-137">Ortam değişkenini ayarlayarak `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="55ce0-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="55ce0-138">DWORD kayıt defteri ayarı ThrowUnobservedTaskExceptions değer = 1 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="55ce0-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55ce0-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="55ce0-139">Example</span></span>  
 <span data-ttu-id="55ce0-140">Aşağıdaki örnek, görevlerde özel durumları atma bir uygulama yapılandırma dosyası kullanarak etkinleştirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="55ce0-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="55ce0-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="55ce0-141">Example</span></span>  
 <span data-ttu-id="55ce0-142">Aşağıdaki örnek nasıl gözetimsiz bir görevden özel durum gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ce0-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="55ce0-143">Kodun düzgün çalışması için yayımlanmış bir program olarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="55ce0-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="55ce0-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55ce0-144">See also</span></span>
- [<span data-ttu-id="55ce0-145">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="55ce0-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="55ce0-146">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="55ce0-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
