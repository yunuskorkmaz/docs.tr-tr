---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 28ef6e12c82cf5ca56962756b9ea964d0ae9baaa
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216168"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="810c4-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="810c4-102">loadFromContext MDA</span></span>
<span data-ttu-id="810c4-103">`loadFromContext` yönetilen hata ayıklama Yardımcısı (MDA), bir derleme `LoadFrom` bağlamına yüklenirse etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="810c4-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="810c4-104">Bu durum, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya başka benzer yöntemlerin çağrılması sonucu olarak ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="810c4-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="810c4-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="810c4-105">Symptoms</span></span>  
 <span data-ttu-id="810c4-106">Bazı yükleyici yöntemlerinin kullanımı, derlemelerin `LoadFrom` bağlamına yüklenmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="810c4-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="810c4-107">Bu bağlamın kullanılması serileştirme, atama ve bağımlılık çözümlemesi için beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="810c4-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="810c4-108">Genel olarak, bu sorunlardan kaçınmak için derlemelerin `Load` bağlamına yüklenmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="810c4-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="810c4-109">Bir derlemenin Bu MDA ' dan ne şekilde yüklendiğini belirlemek zordur.</span><span class="sxs-lookup"><span data-stu-id="810c4-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="810c4-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="810c4-110">Cause</span></span>  
 <span data-ttu-id="810c4-111">Genellikle, genel derleme önbelleği veya <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> özelliği gibi `Load` bağlamı dışında bir yoldan yüklenmişse, bir derleme `LoadFrom` bağlamına yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="810c4-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="810c4-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="810c4-112">Resolution</span></span>  
 <span data-ttu-id="810c4-113"><xref:System.Reflection.Assembly.LoadFrom%2A> çağrılarına artık gerek duyulmayan uygulamaları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="810c4-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="810c4-114">Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="810c4-114">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="810c4-115">Derlemeleri genel bütünleştirilmiş kod önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="810c4-115">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="810c4-116">Derlemeleri <xref:System.AppDomain><xref:System.AppDomainSetup.ApplicationBase%2A> dizinine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="810c4-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="810c4-117">Varsayılan etki alanı söz konusu olduğunda <xref:System.AppDomainSetup.ApplicationBase%2A> Dizin, işlemi başlatan yürütülebilir dosyayı içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="810c4-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="810c4-118">Bu, derlemeyi taşımak uygun değilse yeni bir <xref:System.AppDomain> oluşturulmasını de gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="810c4-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="810c4-119">Bağımlı derlemeler çalıştırılabilire göre alt dizinlerde ise, uygulama yapılandırma (. config) dosyanıza veya ikincil uygulama etki alanlarına bir yoklama yolu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="810c4-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="810c4-120">Her durumda, kod <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemini kullanacak şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="810c4-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="810c4-121">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="810c4-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="810c4-122">MDA 'nin CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="810c4-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="810c4-123">Yükleme isteğinin sonucu olarak kullanılan bağlamı bildirir.</span><span class="sxs-lookup"><span data-stu-id="810c4-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="810c4-124">Çıktı</span><span class="sxs-lookup"><span data-stu-id="810c4-124">Output</span></span>  
 <span data-ttu-id="810c4-125">MDA, derlemenin `LoadFrom` bağlamına yüklendiğini bildiriyor.</span><span class="sxs-lookup"><span data-stu-id="810c4-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="810c4-126">Derlemenin basit adını ve yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="810c4-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="810c4-127">Ayrıca, `LoadFrom` bağlamını kullanmaktan kaçınmak için azaltıcı etkenleri de önerir.</span><span class="sxs-lookup"><span data-stu-id="810c4-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="810c4-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="810c4-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="810c4-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="810c4-129">Example</span></span>  
 <span data-ttu-id="810c4-130">Aşağıdaki kod örneğinde, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="810c4-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="810c4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="810c4-131">See also</span></span>

- [<span data-ttu-id="810c4-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="810c4-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
