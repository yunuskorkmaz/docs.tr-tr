---
title: loadFromContext MDA
description: .NET 'teki loadFromContext Managed hata ayıklama Yardımcısı 'nı (MDA), bir derleme LoadFrom bağlamına yüklenirse etkinleştirilir şekilde anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 8d55268f2b2106dde4e488a6f0271fd3b17349da
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051655"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="28865-103">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="28865-103">loadFromContext MDA</span></span>
<span data-ttu-id="28865-104">`loadFromContext`Bağlam içine bir derleme yüklenirse yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir `LoadFrom` .</span><span class="sxs-lookup"><span data-stu-id="28865-104">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="28865-105">Bu durum, çağırma işleminin <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya diğer benzer yöntemlerin sonucu olarak ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="28865-105">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="28865-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="28865-106">Symptoms</span></span>  
 <span data-ttu-id="28865-107">Bazı yükleyici yöntemlerinin kullanımı, derlemelerin bağlamda yüklenmesine neden olabilir `LoadFrom` .</span><span class="sxs-lookup"><span data-stu-id="28865-107">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="28865-108">Bu bağlamın kullanılması serileştirme, atama ve bağımlılık çözümlemesi için beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="28865-108">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="28865-109">Genel olarak, `Load` Bu sorunlardan kaçınmak için derlemelerin bağlamına yüklenmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="28865-109">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="28865-110">Bir derlemenin Bu MDA ' dan ne şekilde yüklendiğini belirlemek zordur.</span><span class="sxs-lookup"><span data-stu-id="28865-110">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="28865-111">Nedeni</span><span class="sxs-lookup"><span data-stu-id="28865-111">Cause</span></span>  
 <span data-ttu-id="28865-112">Genellikle, `LoadFrom` `Load` genel derleme önbelleği veya özelliği gibi bağlam dışındaki bir yoldan yüklenmişse, bir derleme bağlamına yüklenmiştir <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="28865-112">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="28865-113">Çözüm</span><span class="sxs-lookup"><span data-stu-id="28865-113">Resolution</span></span>  
 <span data-ttu-id="28865-114"><xref:System.Reflection.Assembly.LoadFrom%2A>Çağrılara artık gerek duyulmayan uygulamalar için yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="28865-114">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="28865-115">Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="28865-115">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="28865-116">Derlemeleri genel bütünleştirilmiş kod önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="28865-116">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="28865-117">Derlemeleri <xref:System.AppDomainSetup.ApplicationBase%2A> için dizinine yerleştirin <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="28865-117">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="28865-118">Varsayılan etki alanı durumunda <xref:System.AppDomainSetup.ApplicationBase%2A> Dizin, işlemi başlatan yürütülebilir dosyayı içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="28865-118">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="28865-119">Bu, derlemeyi taşımak uygun değilse yeni bir oluşturma işlemi de gerektirebilir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="28865-119">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="28865-120">Bağımlı derlemeler çalıştırılabilire göre alt dizinlerde ise, uygulama yapılandırma (. config) dosyanıza veya ikincil uygulama etki alanlarına bir yoklama yolu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="28865-120">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="28865-121">Her durumda, kod yöntemini kullanacak şekilde değiştirilebilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="28865-121">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="28865-122">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="28865-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="28865-123">MDA 'nin CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="28865-123">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="28865-124">Yükleme isteğinin sonucu olarak kullanılan bağlamı bildirir.</span><span class="sxs-lookup"><span data-stu-id="28865-124">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="28865-125">Çıktı</span><span class="sxs-lookup"><span data-stu-id="28865-125">Output</span></span>  
 <span data-ttu-id="28865-126">MDA, derlemenin bağlama göre yüklendiğini bildirir `LoadFrom` .</span><span class="sxs-lookup"><span data-stu-id="28865-126">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="28865-127">Derlemenin basit adını ve yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="28865-127">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="28865-128">Ayrıca, bağlamını kullanmaktan kaçınmak için azaltıcı etkenleri de önerir `LoadFrom` .</span><span class="sxs-lookup"><span data-stu-id="28865-128">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="28865-129">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="28865-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="28865-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="28865-130">Example</span></span>  
 <span data-ttu-id="28865-131">Aşağıdaki kod örneğinde, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="28865-131">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is
            // located outside of the Load context probing path.
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="28865-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28865-132">See also</span></span>

- [<span data-ttu-id="28865-133">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="28865-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
