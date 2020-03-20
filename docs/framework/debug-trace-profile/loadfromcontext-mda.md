---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: d0090a0272d1c3b6175b351175689df1e1e4fdbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181804"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="4f6ae-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="4f6ae-102">loadFromContext MDA</span></span>
<span data-ttu-id="4f6ae-103">Bir `loadFromContext` derleme `LoadFrom` içeriğe yüklenirse yönetilen hata ayıklama yardımcısı (MDA) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="4f6ae-104">Bu durum arama <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya diğer benzer yöntemlerin bir sonucu olarak oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4f6ae-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="4f6ae-105">Symptoms</span></span>  
 <span data-ttu-id="4f6ae-106">Bazı yükleyici yöntemlerinin kullanımı derlemelerin `LoadFrom` bağlam içinde yüklenmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="4f6ae-107">Bu bağlamın kullanımı serileştirme, döküm ve bağımlılık çözümü için beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="4f6ae-108">Genel olarak, bu sorunları önlemek için `Load` derlemelerin içeriğe yüklenmesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="4f6ae-109">Bu MDA olmadan bir derlemenin hangi içeriğe yüklendiğini belirlemek zordur.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4f6ae-110">Nedeni</span><span class="sxs-lookup"><span data-stu-id="4f6ae-110">Cause</span></span>  
 <span data-ttu-id="4f6ae-111">Genel olarak, bir derleme `LoadFrom` `Load` bağlam dışındaki bir yoldan yüklenmişse, genel derleme önbelleği <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> veya özellik gibi içeriğe yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4f6ae-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="4f6ae-112">Resolution</span></span>  
 <span data-ttu-id="4f6ae-113">Çağrıların artık gerekmeyecek şekilde <xref:System.Reflection.Assembly.LoadFrom%2A> yapılandırıştırın.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="4f6ae-114">Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4f6ae-114">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="4f6ae-115">Derlemeleri genel derleme önbelleğine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-115">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="4f6ae-116">Derlemeleri dizinine <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomain>yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="4f6ae-117">Varsayılan etki alanı söz konusu <xref:System.AppDomainSetup.ApplicationBase%2A> olduğunda, dizin işlemi başlatan yürütülebilir dosyayı içeren dizindir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="4f6ae-118">Bu, derlemeyi taşımak <xref:System.AppDomain> için uygun değilse yeni bir oluşturma yı da gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="4f6ae-119">Uygulama yapılandırmanıza (.config) dosyanıza veya çalıştırılabilir dosyaya göre alt dizinlerde bağımlı derlemeler varsa ikincil uygulama etki adlarına bir sondalama yolu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="4f6ae-120">Her durumda, kod <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi kullanmak için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4f6ae-121">Çalışma Süresi üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="4f6ae-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="4f6ae-122">MDA'nın CLR üzerinde herhangi bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="4f6ae-123">Yük isteği nin sonucu olarak kullanılan bağlamı bildirir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4f6ae-124">Çıktı</span><span class="sxs-lookup"><span data-stu-id="4f6ae-124">Output</span></span>  
 <span data-ttu-id="4f6ae-125">MDA, derlemenin bağlam içine `LoadFrom` yüklendiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="4f6ae-126">Bu derleme ve yol basit adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="4f6ae-127">Ayrıca `LoadFrom` bağlamı kullanmaktan kaçınmak için azaltıcı etkenler önerir.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4f6ae-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4f6ae-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="4f6ae-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f6ae-129">Example</span></span>  
 <span data-ttu-id="4f6ae-130">Aşağıdaki kod örneği, bu MDA'yı etkinleştirebilecek bir durumu gösterir:</span><span class="sxs-lookup"><span data-stu-id="4f6ae-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f6ae-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f6ae-131">See also</span></span>

- [<span data-ttu-id="4f6ae-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4f6ae-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
