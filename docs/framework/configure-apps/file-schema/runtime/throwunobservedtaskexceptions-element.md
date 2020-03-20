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
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153821"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="802b7-102">\<ThrowUnobservedTaskExceptions> Öğesi</span><span class="sxs-lookup"><span data-stu-id="802b7-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="802b7-103">İşlenmemiş görev özel durumlarının çalışan bir işlemi sonlandırıp sonlandırmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="802b7-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="802b7-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="802b7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="802b7-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="802b7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="802b7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span><span class="sxs-lookup"><span data-stu-id="802b7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="802b7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="802b7-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="802b7-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="802b7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="802b7-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="802b7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="802b7-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="802b7-110">Attributes</span></span>  
  
|<span data-ttu-id="802b7-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="802b7-111">Attribute</span></span>|<span data-ttu-id="802b7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="802b7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="802b7-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="802b7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="802b7-114">İşlenmemiş görev özel durumlarının yürütme işlemini sonlandırıp sonlandırmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="802b7-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="802b7-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="802b7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="802b7-116">Değer</span><span class="sxs-lookup"><span data-stu-id="802b7-116">Value</span></span>|<span data-ttu-id="802b7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="802b7-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="802b7-118">İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırmaz.</span><span class="sxs-lookup"><span data-stu-id="802b7-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="802b7-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="802b7-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="802b7-120">İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="802b7-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="802b7-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="802b7-121">Child Elements</span></span>  
 <span data-ttu-id="802b7-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="802b7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="802b7-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="802b7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="802b7-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="802b7-124">Element</span></span>|<span data-ttu-id="802b7-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="802b7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="802b7-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="802b7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="802b7-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="802b7-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="802b7-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="802b7-128">Remarks</span></span>  
 <span data-ttu-id="802b7-129">Bir <xref:System.Threading.Tasks.Task> özel durumla ilişkili bir özel durum gözlenmemişse, işlem yapılmaz, <xref:System.Threading.Tasks.Task.Wait%2A> üst <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> öğe eklenmez ve özellik okunmamışsa görev özel durumu gözlenmemiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="802b7-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="802b7-130">.NET Framework 4'te, varsayılan <xref:System.Threading.Tasks.Task> olarak, gözlenmeyen bir özel durum varsa, çöp toplanmışsa, sonlandırıcı bir özel durum atar ve işlemi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="802b7-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="802b7-131">Sürecin sona ermesi çöp toplama ve sonuçlandırma zamanlaması ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="802b7-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="802b7-132">Geliştiricilerin görevlere dayalı eşzamanlı kod yazmasını kolaylaştırmak için .NET Framework 4.5 bu varsayılan davranışı gözlenmemiş özel durumlar için değiştirir.</span><span class="sxs-lookup"><span data-stu-id="802b7-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="802b7-133">Gözlenmeyen özel durumlar <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> yine de olayın yükseltilmesine neden olur, ancak varsayılan olarak işlem sonlandırmaz.</span><span class="sxs-lookup"><span data-stu-id="802b7-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="802b7-134">Bunun yerine, olay büyütüldükten sonra, bir olay işleyicisinin özel durumu gözlemleyip izlemediğine bakılmaksızın özel durum yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="802b7-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="802b7-135">.NET Framework 4.5'te, bir uygulama yapılandırma dosyasındaki [ \<ThrowUnobservedTaskExceptions> öğesini](throwunobservedtaskexceptions-element.md) kullanarak .NET Framework 4'ün özel durum atma davranışını etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="802b7-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="802b7-136">Özel durum davranışını aşağıdaki yollardan birinde de belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="802b7-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="802b7-137">Çevre değişkenini `COMPlus_ThrowUnobservedTaskExceptions` `set COMPlus_ThrowUnobservedTaskExceptions=1`ayarlayarak ( ).</span><span class="sxs-lookup"><span data-stu-id="802b7-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="802b7-138">Kayıt defteri DWORD değeri ThrowUnobservedTaskExceptions = 1 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ayarlayarak . NETFramework anahtarı.</span><span class="sxs-lookup"><span data-stu-id="802b7-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="802b7-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="802b7-139">Example</span></span>  
 <span data-ttu-id="802b7-140">Aşağıdaki örnekte, bir uygulama yapılandırma dosyası kullanarak görevlerde özel durumların atılması nasıl etkinleştirilir gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="802b7-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="802b7-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="802b7-141">Example</span></span>  
 <span data-ttu-id="802b7-142">Aşağıdaki örnek, gözlenmeyen bir özel durum bir görevden nasıl atıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="802b7-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="802b7-143">Kodun düzgün çalışması için serbest bırakılmış bir program olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="802b7-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="802b7-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="802b7-144">See also</span></span>

- [<span data-ttu-id="802b7-145">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="802b7-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="802b7-146">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="802b7-146">Configuration File Schema</span></span>](../index.md)
