---
title: memberInfoCacheCreation MDA
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3b65ecc226c1caf7b53d746f0583e1f57c7d8c1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052464"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="294fa-102">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="294fa-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="294fa-103">Yönetilen `memberInfoCacheCreation` hata ayıklama Yardımcısı (MDA), bir <xref:System.Reflection.MemberInfo> önbellek oluşturulduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="294fa-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="294fa-104">Bu, kaynak maliyetli yansıma özelliklerini kullanan bir programın güçlü bir göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="294fa-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="294fa-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="294fa-105">Symptoms</span></span>  
 <span data-ttu-id="294fa-106">Program kaynak maliyetli yansıma kullandığından programın çalışma kümesi artar.</span><span class="sxs-lookup"><span data-stu-id="294fa-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="294fa-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="294fa-107">Cause</span></span>  
 <span data-ttu-id="294fa-108"><xref:System.Reflection.MemberInfo> Nesneleri içeren yansıma işlemleri, soğuk sayfalarda depolanan meta verileri okuması ve genel olarak programın bazı tür geç bağlantılı senaryolar kullandığını belirtmesi gerektiğinden kaynak maliyetli olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="294fa-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="294fa-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="294fa-109">Resolution</span></span>  
 <span data-ttu-id="294fa-110">Bu MDA ' ı etkinleştirerek ve sonra kodunuzu bir hata ayıklayıcıda çalıştırarak veya MDA etkinleştirildiğinde bir hata ayıklayıcı ile iliştirerek, yansıma programınızda nerede kullanıldığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="294fa-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="294fa-111">Bir hata ayıklayıcı altında, <xref:System.Reflection.MemberInfo> önbelleğin nerede oluşturulduğunu gösteren bir yığın izlemesi alırsınız ve bu noktada programınızın yansıma kullandığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="294fa-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="294fa-112">Çözüm, kodun hedeflerine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="294fa-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="294fa-113">Bu MDA, programınızın geç bağlanan bir senaryoya sahip olduğunu uyarır.</span><span class="sxs-lookup"><span data-stu-id="294fa-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="294fa-114">Erken bağlantılı bir senaryoyu değiştirebilir veya geç bağlantılı senaryonun performansını göz önünde bulundurup belirleyemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="294fa-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="294fa-115">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="294fa-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="294fa-116">Bu mda, oluşturulan her <xref:System.Reflection.MemberInfo> önbellek için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="294fa-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="294fa-117">Performans etkisi göz ardı edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="294fa-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="294fa-118">Çıkış</span><span class="sxs-lookup"><span data-stu-id="294fa-118">Output</span></span>  
 <span data-ttu-id="294fa-119">MDA, <xref:System.Reflection.MemberInfo> önbelleğin oluşturulduğunu belirten bir ileti çıkışı verir.</span><span class="sxs-lookup"><span data-stu-id="294fa-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="294fa-120">Programınızın yansıma kullandığını gösteren bir yığın izlemesi almak için bir hata ayıklayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="294fa-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="294fa-121">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="294fa-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="294fa-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="294fa-122">Example</span></span>  
 <span data-ttu-id="294fa-123">Bu örnek kod, `memberInfoCacheCreation` MDA öğesini etkinleştirececektir.</span><span class="sxs-lookup"><span data-stu-id="294fa-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="294fa-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="294fa-124">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="294fa-125">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="294fa-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
