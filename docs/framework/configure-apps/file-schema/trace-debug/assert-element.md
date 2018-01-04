---
title: "&lt;Assert&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9670cf0faa3e7f69b8f99b09fa26741991a60481
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltassertgt-element"></a><span data-ttu-id="e554b-102">&lt;Assert&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="e554b-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="e554b-103">Bir ileti kutusu çağırdığınızda görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemi; ayrıca iletileri yazmak için dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e554b-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="e554b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e554b-104">\<configuration></span></span>  
<span data-ttu-id="e554b-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e554b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e554b-106">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="e554b-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e554b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e554b-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e554b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e554b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e554b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e554b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e554b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e554b-110">Attributes</span></span>  
  
|<span data-ttu-id="e554b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e554b-111">Attribute</span></span>|<span data-ttu-id="e554b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e554b-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="e554b-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e554b-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e554b-114">Görüntülenecek bir ileti kutusunu olup olmadığını belirtir **Debug.Assert** yöntemi hesaplar için **false**.</span><span class="sxs-lookup"><span data-stu-id="e554b-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="e554b-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e554b-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e554b-116">İf ileti yazmak için dosya adını belirtir **Debug.Assert** değerlendiren **false**.</span><span class="sxs-lookup"><span data-stu-id="e554b-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="e554b-117">assertuienabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="e554b-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="e554b-118">Değer</span><span class="sxs-lookup"><span data-stu-id="e554b-118">Value</span></span>|<span data-ttu-id="e554b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e554b-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="e554b-120">İleti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e554b-120">Displays the message box.</span></span> <span data-ttu-id="e554b-121">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e554b-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="e554b-122">İleti kutusu görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="e554b-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e554b-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e554b-123">Child Elements</span></span>  
 <span data-ttu-id="e554b-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="e554b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e554b-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e554b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e554b-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="e554b-126">Element</span></span>|<span data-ttu-id="e554b-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e554b-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e554b-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e554b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e554b-129">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e554b-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e554b-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e554b-130">Remarks</span></span>  
 <span data-ttu-id="e554b-131">Her iki öznitelik  **\<assert >** öğesi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e554b-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="e554b-132">İletileri yazmak için bir dosya belirtmeden ileti kutuları devre dışı bırakabilir veya ileti kutuları etkin bırakarak çalışırken iletiler yazmak için bir dosya belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e554b-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e554b-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="e554b-133">Example</span></span>  
 <span data-ttu-id="e554b-134">Aşağıdaki örnek çağırdığınızda görüntüleme ileti kutuları devre dışı bırakma gösterir **Debug.Assert** ve iletileri yazma `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="e554b-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e554b-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e554b-135">See Also</span></span>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="e554b-136">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e554b-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
