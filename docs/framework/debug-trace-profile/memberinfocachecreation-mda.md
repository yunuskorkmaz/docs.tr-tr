---
title: memberInfoCacheCreation MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d82e77e2a47a9b0feb36ca054c0abcff2721940
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="83142-102">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="83142-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="83142-103">`memberInfoCacheCreation` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş olduğunda bir <xref:System.Reflection.MemberInfo> önbellek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="83142-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="83142-104">Bu bir yapıyor bir program güçlü göstergesidir kaynak açısından pahalı yansıma özelliklerinin kullanımı.</span><span class="sxs-lookup"><span data-stu-id="83142-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="83142-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="83142-105">Symptoms</span></span>  
 <span data-ttu-id="83142-106">Program kaynak açısından pahalı yansıma kullandığından bir program kümesi artar çalışma.</span><span class="sxs-lookup"><span data-stu-id="83142-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="83142-107">Sebep</span><span class="sxs-lookup"><span data-stu-id="83142-107">Cause</span></span>  
 <span data-ttu-id="83142-108">İçeren yansıma işlemleri <xref:System.Reflection.MemberInfo> nesneleri olarak kabul edilir çünkü soğuk sayfalarında depolanan meta veri okuması gerekir ve program Genel geldikleri pahalı kaynak geç bağlama senaryosu herhangi bir tür kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="83142-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="83142-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="83142-109">Resolution</span></span>  
 <span data-ttu-id="83142-110">Burada yansıma programınıza bu MDA etkinleştirme ve ardından bir hata ayıklayıcıda kodunuzu çalıştırmaya veya MDA etkinleştirilirken bir hata ayıklayıcısı ile ekleme kullanılıyor belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83142-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="83142-111">Hata ayıklayıcı altında yeri gösteren bir yığın izlemesi alırsınız <xref:System.Reflection.MemberInfo> önbellek oluşturuldu ve buradan programınızı yansıma burada kullanarak belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83142-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="83142-112">Çözümleme kod amaçlarını bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="83142-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="83142-113">Bu MDA programınızı geç bağlama senaryosu olduğunu uyarır.</span><span class="sxs-lookup"><span data-stu-id="83142-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="83142-114">Erken bağlama senaryosu değiştirin veya geç bağlama senaryosu performansını göz önünde bulundurun varsa belirlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83142-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="83142-115">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="83142-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="83142-116">Bu MDA için etkinleştirilen her <xref:System.Reflection.MemberInfo> oluşturulan önbelleği.</span><span class="sxs-lookup"><span data-stu-id="83142-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="83142-117">Performans etkisi önemsizdir.</span><span class="sxs-lookup"><span data-stu-id="83142-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="83142-118">Çıkış</span><span class="sxs-lookup"><span data-stu-id="83142-118">Output</span></span>  
 <span data-ttu-id="83142-119">MDA belirten bir ileti çıkarır <xref:System.Reflection.MemberInfo> önbellek oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="83142-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="83142-120">Bir hata ayıklayıcısı programınızı yansıma burada kullanarak gösteren bir yığın izlemesi almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="83142-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="83142-121">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="83142-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="83142-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="83142-122">Example</span></span>  
 <span data-ttu-id="83142-123">Bu örnek kod etkinleştirecek `memberInfoCacheCreation` MDA.</span><span class="sxs-lookup"><span data-stu-id="83142-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```  
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="83142-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83142-124">See Also</span></span>  
 <xref:System.Reflection.MemberInfo>  
 [<span data-ttu-id="83142-125">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="83142-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
