---
title: memberInfoCacheCreation MDA
description: .NET 'teki memberInfoCacheCreation Managed hata ayıklama Yardımcısı 'nı (MDA), bir MemberInfo önbelleği oluşturulduğunda etkinleştirilen şekilde anlayın.
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
ms.openlocfilehash: c48be7ac8632b8072981be01e01997ee8c34b6b3
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051148"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="747f2-103">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="747f2-103">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="747f2-104">`memberInfoCacheCreation`Yönetilen hata ayıklama Yardımcısı (MDA), bir <xref:System.Reflection.MemberInfo> önbellek oluşturulduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="747f2-104">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="747f2-105">Bu, kaynak maliyetli yansıma özelliklerini kullanan bir programın güçlü bir göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="747f2-105">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="747f2-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="747f2-106">Symptoms</span></span>  
 <span data-ttu-id="747f2-107">Program kaynak maliyetli yansıma kullandığından programın çalışma kümesi artar.</span><span class="sxs-lookup"><span data-stu-id="747f2-107">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="747f2-108">Nedeni</span><span class="sxs-lookup"><span data-stu-id="747f2-108">Cause</span></span>  
 <span data-ttu-id="747f2-109">Nesneleri içeren yansıma işlemleri, <xref:System.Reflection.MemberInfo> soğuk sayfalarda depolanan meta verileri okuması ve genel olarak programın bazı tür geç bağlantılı senaryolar kullandığını belirtmesi gerektiğinden kaynak maliyetli olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="747f2-109">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="747f2-110">Çözüm</span><span class="sxs-lookup"><span data-stu-id="747f2-110">Resolution</span></span>  
 <span data-ttu-id="747f2-111">Bu MDA ' ı etkinleştirerek ve sonra kodunuzu bir hata ayıklayıcıda çalıştırarak veya MDA etkinleştirildiğinde bir hata ayıklayıcı ile iliştirerek, yansıma programınızda nerede kullanıldığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="747f2-111">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="747f2-112">Bir hata ayıklayıcı altında, önbelleğin nerede oluşturulduğunu gösteren bir yığın izlemesi alırsınız ve bu noktada <xref:System.Reflection.MemberInfo> programınızın yansıma kullandığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="747f2-112">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="747f2-113">Çözüm, kodun hedeflerine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="747f2-113">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="747f2-114">Bu MDA, programınızın geç bağlanan bir senaryoya sahip olduğunu uyarır.</span><span class="sxs-lookup"><span data-stu-id="747f2-114">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="747f2-115">Erken bağlantılı bir senaryoyu değiştirebilir veya geç bağlantılı senaryonun performansını göz önünde bulundurup belirleyemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="747f2-115">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="747f2-116">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="747f2-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="747f2-117">Bu MDA, oluşturulan her önbellek için etkinleştirilir <xref:System.Reflection.MemberInfo> .</span><span class="sxs-lookup"><span data-stu-id="747f2-117">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="747f2-118">Performans etkisi göz ardı edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="747f2-118">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="747f2-119">Çıktı</span><span class="sxs-lookup"><span data-stu-id="747f2-119">Output</span></span>  
 <span data-ttu-id="747f2-120">MDA, önbelleğin oluşturulduğunu belirten bir ileti çıkışı verir <xref:System.Reflection.MemberInfo> .</span><span class="sxs-lookup"><span data-stu-id="747f2-120">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="747f2-121">Programınızın yansıma kullandığını gösteren bir yığın izlemesi almak için bir hata ayıklayıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="747f2-121">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="747f2-122">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="747f2-122">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="747f2-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="747f2-123">Example</span></span>  
 <span data-ttu-id="747f2-124">Bu örnek kod, MDA öğesini etkinleştirececektir `memberInfoCacheCreation` .</span><span class="sxs-lookup"><span data-stu-id="747f2-124">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="747f2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="747f2-125">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="747f2-126">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="747f2-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
