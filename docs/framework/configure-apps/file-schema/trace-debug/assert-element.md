---
description: 'Daha fazla bilgi edinin: <assert> öğesi'
title: <assert> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: ce8000b30569d0e5ce47a77fbccd4bec833bb5be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725993"
---
# <a name="assert-element"></a><span data-ttu-id="a3804-103">\<assert> Öğesi</span><span class="sxs-lookup"><span data-stu-id="a3804-103">\<assert> Element</span></span>

<span data-ttu-id="a3804-104">Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3804-104">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="a3804-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a3804-105">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3804-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3804-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a3804-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3804-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3804-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a3804-108">Attributes</span></span>  
  
|<span data-ttu-id="a3804-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a3804-109">Attribute</span></span>|<span data-ttu-id="a3804-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3804-110">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="a3804-111">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a3804-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a3804-112">**Debug. onaylama** yöntemi **false** olarak değerlendirilirse bir ileti kutusu görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3804-112">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="a3804-113">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a3804-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a3804-114">**Hata ayıkla. onaylama** **yanlış** olarak değerlendirilirse iletinin yazılacağı dosyanın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3804-114">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="a3804-115">AssertUiEnabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="a3804-115">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="a3804-116">Değer</span><span class="sxs-lookup"><span data-stu-id="a3804-116">Value</span></span>|<span data-ttu-id="a3804-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3804-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="a3804-118">İleti kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a3804-118">Displays the message box.</span></span> <span data-ttu-id="a3804-119">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="a3804-119">This is the default.</span></span>|  
|`false`|<span data-ttu-id="a3804-120">İleti kutusunu görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="a3804-120">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3804-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3804-121">Child Elements</span></span>  

 <span data-ttu-id="a3804-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="a3804-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3804-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3804-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a3804-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3804-124">Element</span></span>|<span data-ttu-id="a3804-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3804-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a3804-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a3804-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a3804-127">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3804-127">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3804-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3804-128">Remarks</span></span>  

 <span data-ttu-id="a3804-129">Öğesi içindeki her iki öznitelik de **\<assert>** isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a3804-129">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="a3804-130">İletileri yazmak için bir dosya belirtmeden ileti kutularını devre dışı bırakabilir veya ileti kutularından etkin bırakarak mesaj yazılacak bir dosya belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3804-130">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3804-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3804-131">Example</span></span>  

 <span data-ttu-id="a3804-132">Aşağıdaki örnek, **hata ayıklama. onayı** çağırdığınızda ileti kutularının nasıl devre dışı bırakılacağını gösterir ve iletileri öğesine yazın `c:\log.txt` .</span><span class="sxs-lookup"><span data-stu-id="a3804-132">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3804-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3804-133">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="a3804-134">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="a3804-134">Trace and Debug Settings Schema</span></span>](index.md)
