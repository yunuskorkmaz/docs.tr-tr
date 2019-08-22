---
title: <ThrowUnobservedTaskExceptions> Öğesi
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
ms.openlocfilehash: 876452a0a56d10f169526138cdbbbd153572f457
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658843"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="91932-102">\<ThrowUnobservedTaskExceptions > öğesi</span><span class="sxs-lookup"><span data-stu-id="91932-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="91932-103">İşlenmemiş görev özel durumlarının çalışan bir işlemi sonlandırmayı gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="91932-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="91932-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="91932-104">\<configuration></span></span>  
<span data-ttu-id="91932-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="91932-105">\<runtime></span></span>  
<span data-ttu-id="91932-106">\<ThrowUnobservedTaskExceptions ></span><span class="sxs-lookup"><span data-stu-id="91932-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91932-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91932-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91932-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="91932-108">Attributes and Elements</span></span>  
 <span data-ttu-id="91932-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91932-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91932-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="91932-110">Attributes</span></span>  
  
|<span data-ttu-id="91932-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="91932-111">Attribute</span></span>|<span data-ttu-id="91932-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91932-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="91932-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="91932-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="91932-114">İşlenmemiş görev özel durumlarının çalışan işlemi sonlandırmayı gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="91932-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="91932-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="91932-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="91932-116">Değer</span><span class="sxs-lookup"><span data-stu-id="91932-116">Value</span></span>|<span data-ttu-id="91932-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91932-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="91932-118">İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="91932-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="91932-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="91932-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="91932-120">İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="91932-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91932-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="91932-121">Child Elements</span></span>  
 <span data-ttu-id="91932-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="91932-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91932-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="91932-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91932-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="91932-124">Element</span></span>|<span data-ttu-id="91932-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91932-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="91932-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="91932-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="91932-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="91932-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="91932-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91932-128">Remarks</span></span>  
 <span data-ttu-id="91932-129">İle <xref:System.Threading.Tasks.Task> ilişkili bir özel durum gözlemlenmeyen bir işlem yok <xref:System.Threading.Tasks.Task.Wait%2A> , üst öğe iliştirilmemiş ve <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özellik okunamadı, görev özel durumu gözlemlenmemiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="91932-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="91932-130">.NET Framework 4 ' te, varsayılan olarak, gözlemlenen olmayan <xref:System.Threading.Tasks.Task> bir özel durum atık olarak toplanmışsa Sonlandırıcı bir özel durum oluşturur ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="91932-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="91932-131">İşlemin sonlandırılması çöp toplama ve sonlandırma zamanlaması tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="91932-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="91932-132">Geliştiricilerin görevlere göre zaman uyumsuz kod yazmasını kolaylaştırmak için .NET Framework 4,5, gözlemlenen özel durumlar için bu varsayılan davranışı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="91932-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="91932-133">Gözlemlenen özel durumlar hala <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> etkinliğin oluşturulmasına neden olur, ancak varsayılan olarak işlem sonlanmaz.</span><span class="sxs-lookup"><span data-stu-id="91932-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="91932-134">Bunun yerine, bir olay işleyicisinin özel durumu görmediğine bakılmaksızın, olay oluşturulduktan sonra özel durum yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="91932-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="91932-135">.NET Framework 4,5 ' de, bir özel durum oluşturan .NET Framework 4 davranışını etkinleştirmek için bir uygulama yapılandırma dosyasında [ \<ThrowUnobservedTaskExceptions > öğesini](throwunobservedtaskexceptions-element.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91932-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="91932-136">Özel durum davranışını aşağıdaki yollarla da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="91932-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="91932-137">Ortam değişkenini `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`) ayarlayarak.</span><span class="sxs-lookup"><span data-stu-id="91932-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="91932-138">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\içinde ThrowUnobservedTaskExceptions = 1 kayıt defteri DWORD değerini ayarlayarak. NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="91932-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91932-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="91932-139">Example</span></span>  
 <span data-ttu-id="91932-140">Aşağıdaki örnek, bir uygulama yapılandırma dosyası kullanarak görevlerde özel durumların üretilmesini nasıl etkinleştireceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="91932-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="91932-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="91932-141">Example</span></span>  
 <span data-ttu-id="91932-142">Aşağıdaki örnekte, bir görevden gözlemlenen bir özel durumun nasıl oluşturulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="91932-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="91932-143">Kod, doğru bir şekilde çalışması için yayınlanmış bir program olarak çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91932-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="91932-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91932-144">See also</span></span>

- [<span data-ttu-id="91932-145">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="91932-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="91932-146">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="91932-146">Configuration File Schema</span></span>](../index.md)
