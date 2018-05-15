---
title: '&lt;Assert&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ab1644d23e4d6d78b62e701902e5ec39e134b38b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltassertgt-element"></a><span data-ttu-id="3615a-102">&lt;Assert&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="3615a-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="3615a-103">Bir ileti kutusu çağırdığınızda görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yöntemi; ayrıca iletileri yazmak için dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3615a-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="3615a-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3615a-104">\<configuration></span></span>  
<span data-ttu-id="3615a-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="3615a-105">\<system.diagnostics></span></span>  
<span data-ttu-id="3615a-106">\<Assert ></span><span class="sxs-lookup"><span data-stu-id="3615a-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3615a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3615a-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3615a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3615a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3615a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3615a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3615a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3615a-110">Attributes</span></span>  
  
|<span data-ttu-id="3615a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3615a-111">Attribute</span></span>|<span data-ttu-id="3615a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3615a-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="3615a-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3615a-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3615a-114">Görüntülenecek bir ileti kutusunu olup olmadığını belirtir **Debug.Assert** yöntemi hesaplar için **false**.</span><span class="sxs-lookup"><span data-stu-id="3615a-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="3615a-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3615a-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3615a-116">İf ileti yazmak için dosya adını belirtir **Debug.Assert** değerlendiren **false**.</span><span class="sxs-lookup"><span data-stu-id="3615a-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="3615a-117">assertuienabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="3615a-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="3615a-118">Değer</span><span class="sxs-lookup"><span data-stu-id="3615a-118">Value</span></span>|<span data-ttu-id="3615a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3615a-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="3615a-120">İleti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3615a-120">Displays the message box.</span></span> <span data-ttu-id="3615a-121">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3615a-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="3615a-122">İleti kutusu görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="3615a-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3615a-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3615a-123">Child Elements</span></span>  
 <span data-ttu-id="3615a-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="3615a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3615a-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3615a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3615a-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="3615a-126">Element</span></span>|<span data-ttu-id="3615a-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3615a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3615a-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3615a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3615a-129">Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3615a-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3615a-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3615a-130">Remarks</span></span>  
 <span data-ttu-id="3615a-131">Her iki öznitelik  **\<assert >** öğesi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3615a-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="3615a-132">İletileri yazmak için bir dosya belirtmeden ileti kutuları devre dışı bırakabilir veya ileti kutuları etkin bırakarak çalışırken iletiler yazmak için bir dosya belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3615a-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3615a-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="3615a-133">Example</span></span>  
 <span data-ttu-id="3615a-134">Aşağıdaki örnek çağırdığınızda görüntüleme ileti kutuları devre dışı bırakma gösterir **Debug.Assert** ve iletileri yazma `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="3615a-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3615a-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3615a-135">See Also</span></span>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="3615a-136">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3615a-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
