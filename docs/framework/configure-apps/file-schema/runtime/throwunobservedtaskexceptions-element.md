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
ms.openlocfilehash: 012c2e70e66015bc317606a7eea07812b5df26e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183929"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="7dbe3-102">\<ThrowUnobservedTaskExceptions> Öğesi</span><span class="sxs-lookup"><span data-stu-id="7dbe3-102">\<ThrowUnobservedTaskExceptions> Element</span></span>

<span data-ttu-id="7dbe3-103">İşlenmemiş görev özel durumlarının çalışan bir işlemi sonlandırmayı gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a><span data-ttu-id="7dbe3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7dbe3-104">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7dbe3-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7dbe3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7dbe3-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7dbe3-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7dbe3-107">Attributes</span></span>  
  
|<span data-ttu-id="7dbe3-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7dbe3-108">Attribute</span></span>|<span data-ttu-id="7dbe3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dbe3-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7dbe3-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="7dbe3-111">İşlenmemiş görev özel durumlarının çalışan işlemi sonlandırmayı gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-111">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7dbe3-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7dbe3-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="7dbe3-113">Değer</span><span class="sxs-lookup"><span data-stu-id="7dbe3-113">Value</span></span>|<span data-ttu-id="7dbe3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dbe3-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7dbe3-115">İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-115">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="7dbe3-116">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="7dbe3-117">İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-117">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7dbe3-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7dbe3-118">Child Elements</span></span>  

 <span data-ttu-id="7dbe3-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7dbe3-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7dbe3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7dbe3-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="7dbe3-121">Element</span></span>|<span data-ttu-id="7dbe3-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dbe3-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7dbe3-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7dbe3-124">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-124">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="7dbe3-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7dbe3-125">Remarks</span></span>  

 <span data-ttu-id="7dbe3-126">İle ilişkili bir özel durum <xref:System.Threading.Tasks.Task> gözlemlenmeyen bir <xref:System.Threading.Tasks.Task.Wait%2A> işlem yok, üst öğe iliştirilmemiş ve <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özellik okunamadı, görev özel durumu gözlemlenmemiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-126">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="7dbe3-127">.NET Framework 4 ' te, varsayılan olarak, gözlemlenen olmayan bir <xref:System.Threading.Tasks.Task> özel durum atık olarak toplanmışsa Sonlandırıcı bir özel durum oluşturur ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-127">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="7dbe3-128">İşlemin sonlandırılması çöp toplama ve sonlandırma zamanlaması tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-128">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="7dbe3-129">Geliştiricilerin görevlere göre zaman uyumsuz kod yazmasını kolaylaştırmak için .NET Framework 4,5, gözlemlenen özel durumlar için bu varsayılan davranışı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-129">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="7dbe3-130">Gözlemlenen özel durumlar hala etkinliğin oluşturulmasına neden olur <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> , ancak varsayılan olarak işlem sonlanmaz.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-130">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="7dbe3-131">Bunun yerine, bir olay işleyicisinin özel durumu görmediğine bakılmaksızın, olay oluşturulduktan sonra özel durum yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-131">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="7dbe3-132">.NET Framework 4,5 ' de, bir özel durum oluşturan .NET Framework 4 davranışını etkinleştirmek için bir uygulama yapılandırma dosyasındaki [ \<ThrowUnobservedTaskExceptions> öğesini](throwunobservedtaskexceptions-element.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-132">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="7dbe3-133">Özel durum davranışını aşağıdaki yollarla da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7dbe3-133">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="7dbe3-134">Ortam değişkenini `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ) ayarlayarak.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-134">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="7dbe3-135">ThrowUnobservedTaskExceptions = 1 kayıt defteri DWORD değerini HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft olarak ayarlayarak \\ . NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-135">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dbe3-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="7dbe3-136">Example</span></span>  

 <span data-ttu-id="7dbe3-137">Aşağıdaki örnek, bir uygulama yapılandırma dosyası kullanarak görevlerde özel durumların üretilmesini nasıl etkinleştireceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-137">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="7dbe3-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="7dbe3-138">Example</span></span>  

 <span data-ttu-id="7dbe3-139">Aşağıdaki örnekte, bir görevden gözlemlenen bir özel durumun nasıl oluşturulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-139">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="7dbe3-140">Kod, doğru bir şekilde çalışması için yayınlanmış bir program olarak çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-140">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7dbe3-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dbe3-141">See also</span></span>

- [<span data-ttu-id="7dbe3-142">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="7dbe3-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7dbe3-143">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="7dbe3-143">Configuration File Schema</span></span>](../index.md)
