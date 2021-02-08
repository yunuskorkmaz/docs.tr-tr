---
description: 'Daha fazla bilgi edinin: <ThrowUnobservedTaskExceptions> öğesi'
title: <ThrowUnobservedTaskExceptions> Öğesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: 53f3f1275ea8419bed52fd73726c043e1c49eed7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802404"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="60896-103">\<ThrowUnobservedTaskExceptions> Öğesi</span><span class="sxs-lookup"><span data-stu-id="60896-103">\<ThrowUnobservedTaskExceptions> Element</span></span>

<span data-ttu-id="60896-104">İşlenmemiş görev özel durumlarının çalışan bir işlemi sonlandırmayı gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60896-104">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a><span data-ttu-id="60896-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="60896-105">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60896-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60896-106">Attributes and Elements</span></span>  

 <span data-ttu-id="60896-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60896-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60896-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60896-108">Attributes</span></span>  
  
|<span data-ttu-id="60896-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="60896-109">Attribute</span></span>|<span data-ttu-id="60896-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60896-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="60896-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="60896-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="60896-112">İşlenmemiş görev özel durumlarının çalışan işlemi sonlandırmayı gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60896-112">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="60896-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="60896-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="60896-114">Değer</span><span class="sxs-lookup"><span data-stu-id="60896-114">Value</span></span>|<span data-ttu-id="60896-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60896-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="60896-116">İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="60896-116">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="60896-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="60896-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="60896-118">İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="60896-118">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60896-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60896-119">Child Elements</span></span>  

 <span data-ttu-id="60896-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="60896-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60896-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60896-121">Parent Elements</span></span>  
  
|<span data-ttu-id="60896-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="60896-122">Element</span></span>|<span data-ttu-id="60896-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60896-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="60896-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="60896-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="60896-125">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="60896-125">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="60896-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60896-126">Remarks</span></span>  

 <span data-ttu-id="60896-127">İle ilişkili bir özel durum <xref:System.Threading.Tasks.Task> gözlemlenmeyen bir <xref:System.Threading.Tasks.Task.Wait%2A> işlem yok, üst öğe iliştirilmemiş ve <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özellik okunamadı, görev özel durumu gözlemlenmemiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="60896-127">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="60896-128">.NET Framework 4 ' te, varsayılan olarak, gözlemlenen olmayan bir <xref:System.Threading.Tasks.Task> özel durum atık olarak toplanmışsa Sonlandırıcı bir özel durum oluşturur ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="60896-128">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="60896-129">İşlemin sonlandırılması çöp toplama ve sonlandırma zamanlaması tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="60896-129">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="60896-130">Geliştiricilerin görevlere göre zaman uyumsuz kod yazmasını kolaylaştırmak için .NET Framework 4,5, gözlemlenen özel durumlar için bu varsayılan davranışı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="60896-130">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="60896-131">Gözlemlenen özel durumlar hala etkinliğin oluşturulmasına neden olur <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> , ancak varsayılan olarak işlem sonlanmaz.</span><span class="sxs-lookup"><span data-stu-id="60896-131">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="60896-132">Bunun yerine, bir olay işleyicisinin özel durumu görmediğine bakılmaksızın, olay oluşturulduktan sonra özel durum yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="60896-132">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="60896-133">.NET Framework 4,5 ' de, bir özel durum oluşturan .NET Framework 4 davranışını etkinleştirmek için bir uygulama yapılandırma dosyasındaki [ \<ThrowUnobservedTaskExceptions> öğesini](throwunobservedtaskexceptions-element.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60896-133">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="60896-134">Özel durum davranışını aşağıdaki yollarla da belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60896-134">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="60896-135">Ortam değişkenini `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ) ayarlayarak.</span><span class="sxs-lookup"><span data-stu-id="60896-135">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="60896-136">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoftkayıt defteri DWORD değerini ThrowUnobservedTaskExceptions = 1 olarak ayarlayarak \\ . NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="60896-136">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60896-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="60896-137">Example</span></span>  

 <span data-ttu-id="60896-138">Aşağıdaki örnek, bir uygulama yapılandırma dosyası kullanarak görevlerde özel durumların üretilmesini nasıl etkinleştireceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="60896-138">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="60896-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="60896-139">Example</span></span>  

 <span data-ttu-id="60896-140">Aşağıdaki örnekte, bir görevden gözlemlenen bir özel durumun nasıl oluşturulduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="60896-140">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="60896-141">Kod, doğru bir şekilde çalışması için yayınlanmış bir program olarak çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60896-141">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="60896-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60896-142">See also</span></span>

- [<span data-ttu-id="60896-143">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="60896-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="60896-144">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="60896-144">Configuration File Schema</span></span>](../index.md)
