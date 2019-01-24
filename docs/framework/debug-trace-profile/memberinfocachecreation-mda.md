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
ms.openlocfilehash: 028ff1048813ccbc845d5ad3e7f522b492348f87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651038"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="39e24-102">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="39e24-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="39e24-103">`memberInfoCacheCreation` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.Reflection.MemberInfo> önbellek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39e24-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="39e24-104">Bu güçlü bir gösterge yapan bir programın, kaynak açısından pahalı yansıma özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="39e24-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="39e24-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="39e24-105">Symptoms</span></span>  
 <span data-ttu-id="39e24-106">Programı kaynak açısından pahalı yansıma kullandığından bir program kümesi arttıkça çalışma.</span><span class="sxs-lookup"><span data-stu-id="39e24-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="39e24-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="39e24-107">Cause</span></span>  
 <span data-ttu-id="39e24-108">İlgili yansıma işlemleri <xref:System.Reflection.MemberInfo> nesneleri doğrudan sayfalarına depolanan meta veri okuması gerekir ve bunlar programın genel gösterir çünkü pahalı kaynak bazı tür geç bağlama senaryosu kullanarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="39e24-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="39e24-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="39e24-109">Resolution</span></span>  
 <span data-ttu-id="39e24-110">Yansıma programınızda bu MDA etkinleştirme ve ardından bir hata ayıklayıcıda kod çalıştıran veya MDA etkinleştirildiğinde, hata ayıklayıcısı ile iliştirme kullanıldığı yerin belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39e24-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="39e24-111">Hata ayıklayıcı altında nerede gösteren bir yığın izlemesi alırsınız <xref:System.Reflection.MemberInfo> önbellek oluşturuldu ve buradan programınızı yansıma burada kullanarak belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39e24-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="39e24-112">Çözüm üzerinde kod amaçlarını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="39e24-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="39e24-113">Bu MDA, programınızın geç bağlama senaryosu olduğunu uyarır.</span><span class="sxs-lookup"><span data-stu-id="39e24-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="39e24-114">Bir erken bağlanan senaryo değiştirin veya geç bağlanan senaryo performansını göz önünde bulundurun, belirlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39e24-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="39e24-115">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="39e24-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="39e24-116">Bu mda'nın için etkinleştirilen her <xref:System.Reflection.MemberInfo> oluşturulan önbellek.</span><span class="sxs-lookup"><span data-stu-id="39e24-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="39e24-117">Performans etkisini göz ardı edilebilir.</span><span class="sxs-lookup"><span data-stu-id="39e24-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="39e24-118">Çıkış</span><span class="sxs-lookup"><span data-stu-id="39e24-118">Output</span></span>  
 <span data-ttu-id="39e24-119">MDA belirten bir ileti çıkarır <xref:System.Reflection.MemberInfo> önbellek oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="39e24-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="39e24-120">Bir hata ayıklayıcı, programınızın yansıma burada kullanarak gösteren bir yığın izlemesi almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="39e24-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="39e24-121">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="39e24-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="39e24-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="39e24-122">Example</span></span>  
 <span data-ttu-id="39e24-123">Bu örnek kod etkinleştirecek `memberInfoCacheCreation` MDA.</span><span class="sxs-lookup"><span data-stu-id="39e24-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39e24-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39e24-124">See also</span></span>
- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="39e24-125">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="39e24-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
