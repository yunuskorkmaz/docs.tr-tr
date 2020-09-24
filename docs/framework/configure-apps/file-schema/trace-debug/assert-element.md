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
ms.openlocfilehash: eb29701912a45a484b1716195b449e8a97d1d4b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149302"
---
# <a name="assert-element"></a><span data-ttu-id="69c87-102">\<assert> Öğesi</span><span class="sxs-lookup"><span data-stu-id="69c87-102">\<assert> Element</span></span>

<span data-ttu-id="69c87-103">Yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="69c87-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="69c87-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="69c87-104">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69c87-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="69c87-105">Attributes and Elements</span></span>  

 <span data-ttu-id="69c87-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="69c87-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69c87-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="69c87-107">Attributes</span></span>  
  
|<span data-ttu-id="69c87-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="69c87-108">Attribute</span></span>|<span data-ttu-id="69c87-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69c87-109">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="69c87-110">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="69c87-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="69c87-111">**Debug. onaylama** yöntemi **false**olarak değerlendirilirse bir ileti kutusu görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="69c87-111">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="69c87-112">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="69c87-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="69c87-113">**Hata ayıkla. onaylama** **yanlış**olarak değerlendirilirse iletinin yazılacağı dosyanın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="69c87-113">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="69c87-114">AssertUiEnabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="69c87-114">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="69c87-115">Değer</span><span class="sxs-lookup"><span data-stu-id="69c87-115">Value</span></span>|<span data-ttu-id="69c87-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69c87-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="69c87-117">İleti kutusunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="69c87-117">Displays the message box.</span></span> <span data-ttu-id="69c87-118">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="69c87-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="69c87-119">İleti kutusunu görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="69c87-119">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69c87-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="69c87-120">Child Elements</span></span>  

 <span data-ttu-id="69c87-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="69c87-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69c87-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="69c87-122">Parent Elements</span></span>  
  
|<span data-ttu-id="69c87-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="69c87-123">Element</span></span>|<span data-ttu-id="69c87-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69c87-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="69c87-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="69c87-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="69c87-126">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="69c87-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69c87-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69c87-127">Remarks</span></span>  

 <span data-ttu-id="69c87-128">Öğesi içindeki her iki öznitelik de **\<assert>** isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="69c87-128">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="69c87-129">İletileri yazmak için bir dosya belirtmeden ileti kutularını devre dışı bırakabilir veya ileti kutularından etkin bırakarak mesaj yazılacak bir dosya belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69c87-129">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69c87-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="69c87-130">Example</span></span>  

 <span data-ttu-id="69c87-131">Aşağıdaki örnek, **hata ayıklama. onayı** çağırdığınızda ileti kutularının nasıl devre dışı bırakılacağını gösterir ve iletileri öğesine yazın `c:\log.txt` .</span><span class="sxs-lookup"><span data-stu-id="69c87-131">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69c87-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69c87-132">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="69c87-133">İzleme ve hata ayıklama ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="69c87-133">Trace and Debug Settings Schema</span></span>](index.md)
