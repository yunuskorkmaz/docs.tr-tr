---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 632d9119cf32aab66c87e345ec98c6867ed51592
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614377"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="a080f-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="a080f-102">loadFromContext MDA</span></span>
<span data-ttu-id="a080f-103">`loadFromContext` Yönetilen hata ayıklama Yardımcısı (MDA) etkin olduğu bir derleme halinde yüklenmiş ise `LoadFrom` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="a080f-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="a080f-104">Çağırma sonucunda bu durum ortaya çıkabilir <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya diğer benzer yöntemler.</span><span class="sxs-lookup"><span data-stu-id="a080f-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a080f-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="a080f-105">Symptoms</span></span>  
 <span data-ttu-id="a080f-106">Bazı yükleyici yöntemlerin kullanımını içinde yüklenen derlemeler sonuçlanabilir `LoadFrom` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="a080f-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="a080f-107">Bu bağlam kullanımını serileştirme, atama ve bağımlılık çözümlemesi için beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a080f-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="a080f-108">Genel olarak, derlemeleri içine yüklenen önerilir `Load` bu sorunları önlemek için bağlam.</span><span class="sxs-lookup"><span data-stu-id="a080f-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="a080f-109">Hangi bağlamda bir derleme içine bu mda'nın yüklendiğini belirlemek zordur.</span><span class="sxs-lookup"><span data-stu-id="a080f-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a080f-110">Sebep</span><span class="sxs-lookup"><span data-stu-id="a080f-110">Cause</span></span>  
 <span data-ttu-id="a080f-111">Genellikle, bir derleme içine yüklendi `LoadFrom` dışında bir yoldan yüklendiyse bağlam `Load` bağlamı, Genel Derleme Önbelleği gibi veya <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a080f-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a080f-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="a080f-112">Resolution</span></span>  
 <span data-ttu-id="a080f-113">Uygulamaları yapılandır şekilde <xref:System.Reflection.Assembly.LoadFrom%2A> çağrıları artık gerekli.</span><span class="sxs-lookup"><span data-stu-id="a080f-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="a080f-114">Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a080f-114">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="a080f-115">Derlemeleri genel derleme önbelleğine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a080f-115">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="a080f-116">Derlemelerde yerleştirin <xref:System.AppDomainSetup.ApplicationBase%2A> dizinini <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a080f-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="a080f-117">Varsayılan etki alanı, söz konusu olduğunda <xref:System.AppDomainSetup.ApplicationBase%2A> işlemi başlatıldı yürütülebilir dosyayı içeren bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="a080f-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="a080f-118">Bu yeni oluşturma gerektirebilir <xref:System.AppDomain> derleme taşımak uygun değilse.</span><span class="sxs-lookup"><span data-stu-id="a080f-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="a080f-119">Bağımlı derlemelerin yürütülebilir dosyanın göreli alt dizinlerde varsa araştırma yolu, uygulama (.config) yapılandırma dosyası veya ikincil bir uygulama etki alanları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a080f-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="a080f-120">Her durumda, kodu kullanmak için değiştirilebilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a080f-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a080f-121">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="a080f-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="a080f-122">MDA CLR üzerinde hiçbir etkisi yok.</span><span class="sxs-lookup"><span data-stu-id="a080f-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="a080f-123">Bu, yük isteğin sonucu olarak kullanılan bağlam bildirir.</span><span class="sxs-lookup"><span data-stu-id="a080f-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a080f-124">Çıkış</span><span class="sxs-lookup"><span data-stu-id="a080f-124">Output</span></span>  
 <span data-ttu-id="a080f-125">MDA bütünleştirilmiş kod içine yüklenmiş olduğunu bildirdiği `LoadFrom` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="a080f-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="a080f-126">Bu, derleme ve yolun basit adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a080f-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="a080f-127">Ayrıca kullanmaktan kaçınmak için risk azaltma işlemleri önerir `LoadFrom` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="a080f-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a080f-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a080f-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="a080f-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a080f-129">Example</span></span>  
 <span data-ttu-id="a080f-130">Aşağıdaki kod örneği, bu mda'nın etkinleştirebilmek için bir durum gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a080f-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a080f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a080f-131">See also</span></span>

- [<span data-ttu-id="a080f-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="a080f-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
