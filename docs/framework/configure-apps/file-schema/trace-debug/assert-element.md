---
title: <assert> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: 5ba781598542d271f41476b1a1e9d61faeb6ff74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927192"
---
# <a name="assert-element"></a><span data-ttu-id="26282-102">\<onaylama > öğesi</span><span class="sxs-lookup"><span data-stu-id="26282-102">\<assert> Element</span></span>
<span data-ttu-id="26282-103"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="26282-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="26282-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="26282-104">\<configuration></span></span>  
<span data-ttu-id="26282-105">\<System. Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="26282-105">\<system.diagnostics></span></span>  
<span data-ttu-id="26282-106">\<onaylama ></span><span class="sxs-lookup"><span data-stu-id="26282-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26282-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26282-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26282-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="26282-108">Attributes and Elements</span></span>  
 <span data-ttu-id="26282-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="26282-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26282-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="26282-110">Attributes</span></span>  
  
|<span data-ttu-id="26282-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="26282-111">Attribute</span></span>|<span data-ttu-id="26282-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26282-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="26282-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="26282-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="26282-114">**Debug. onaylama** yöntemi **false**olarak değerlendirilirse bir ileti kutusu görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="26282-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="26282-115">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="26282-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="26282-116">**Hata ayıkla. onaylama** **yanlış**olarak değerlendirilirse iletinin yazılacağı dosyanın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="26282-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="26282-117">AssertUiEnabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="26282-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="26282-118">Değer</span><span class="sxs-lookup"><span data-stu-id="26282-118">Value</span></span>|<span data-ttu-id="26282-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26282-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="26282-120">İleti kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="26282-120">Displays the message box.</span></span> <span data-ttu-id="26282-121">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="26282-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="26282-122">İleti kutusunu görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="26282-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26282-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="26282-123">Child Elements</span></span>  
 <span data-ttu-id="26282-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="26282-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26282-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="26282-125">Parent Elements</span></span>  
  
|<span data-ttu-id="26282-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="26282-126">Element</span></span>|<span data-ttu-id="26282-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26282-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="26282-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="26282-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="26282-129">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="26282-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26282-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26282-130">Remarks</span></span>  
 <span data-ttu-id="26282-131">Onaylama > öğesindeki her iki öznitelik  **\<** de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="26282-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="26282-132">İletileri yazmak için bir dosya belirtmeden ileti kutularını devre dışı bırakabilir veya ileti kutularından etkin bırakarak mesaj yazılacak bir dosya belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26282-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26282-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="26282-133">Example</span></span>  
 <span data-ttu-id="26282-134">Aşağıdaki örnek, **hata ayıklama. onayı** çağırdığınızda ileti kutularının nasıl devre dışı bırakılacağını gösterir ve iletileri öğesine `c:\log.txt`yazın.</span><span class="sxs-lookup"><span data-stu-id="26282-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26282-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26282-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="26282-136">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="26282-136">Trace and Debug Settings Schema</span></span>](index.md)
