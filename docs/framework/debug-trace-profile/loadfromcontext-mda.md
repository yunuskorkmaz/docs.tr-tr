---
title: loadFromContext MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0910e4bdd2cc9c99afc55c5f70f4d225a87deb5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="29899-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="29899-102">loadFromContext MDA</span></span>
<span data-ttu-id="29899-103">`loadFromContext` Yönetilen hata ayıklama Yardımcısı (MDA), bir derleme halinde yüklenmiş ise etkinleştirilirse `LoadFrom` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="29899-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="29899-104">Çağırma sonucunda bu durum ortaya çıkabilir <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya benzer diğer yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="29899-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="29899-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="29899-105">Symptoms</span></span>  
 <span data-ttu-id="29899-106">Bazı yükleyici yöntemlerinin kullanımını, yüklenmekte olan derlemelerde sonuçlanabilir `LoadFrom` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="29899-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="29899-107">Bu bağlamda kullanımını seri hale getirme, atama ve bağımlılık çözünürlüğü için beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="29899-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="29899-108">Genel olarak, derlemeler halinde yüklenen önerilir `Load` bu sorunları önlemek için bağlam.</span><span class="sxs-lookup"><span data-stu-id="29899-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="29899-109">Hangi bağlamı bir derleme halinde bu MDA yüklendi belirlemek zordur.</span><span class="sxs-lookup"><span data-stu-id="29899-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="29899-110">Sebep</span><span class="sxs-lookup"><span data-stu-id="29899-110">Cause</span></span>  
 <span data-ttu-id="29899-111">Genellikle, bir derleme halinde yüklendi `LoadFrom` dışında bir yoldan yüklerse bağlam `Load` bağlamı, Genel Derleme Önbelleği gibi veya <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="29899-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="29899-112">Çözüm</span><span class="sxs-lookup"><span data-stu-id="29899-112">Resolution</span></span>  
 <span data-ttu-id="29899-113">Uygulamaları yapılandır şekilde <xref:System.Reflection.Assembly.LoadFrom%2A> çağrıları artık gerekli.</span><span class="sxs-lookup"><span data-stu-id="29899-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="29899-114">Bunu yapmak için aşağıdaki teknikleri kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="29899-114">You can use the following techniques for doing so:</span></span>  
  
-   <span data-ttu-id="29899-115">Derlemeleri genel derleme önbelleğinde yükleyin.</span><span class="sxs-lookup"><span data-stu-id="29899-115">Install assemblies in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="29899-116">Yerleştirin derlemelerde <xref:System.AppDomainSetup.ApplicationBase%2A> için dizin <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="29899-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="29899-117">Varsayılan etki alanı olması durumunda <xref:System.AppDomainSetup.ApplicationBase%2A> işlemi başlatıldı çalıştırılabilir dosyayı içeren bir dizindir.</span><span class="sxs-lookup"><span data-stu-id="29899-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="29899-118">Bu yeni oluşturma gerektirebilir <xref:System.AppDomain> derleme taşımak uygun değilse.</span><span class="sxs-lookup"><span data-stu-id="29899-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
-   <span data-ttu-id="29899-119">Bağımlı derlemeleri yürütülebilir göre alt dizinlerde varsa bir yoklama yolu uygulama yapılandırması (.config) dosyası ya da ikincil uygulama etki alanları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29899-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="29899-120">Her durumda kullanmak için kodu değiştirilebilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="29899-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="29899-121">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="29899-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="29899-122">MDA CLR herhangi bir etkisi yok.</span><span class="sxs-lookup"><span data-stu-id="29899-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="29899-123">Bir yük istek kullanılan bağlam bildirir.</span><span class="sxs-lookup"><span data-stu-id="29899-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="29899-124">Çıkış</span><span class="sxs-lookup"><span data-stu-id="29899-124">Output</span></span>  
 <span data-ttu-id="29899-125">MDA derleme içine yüklenmiş olduğunu bildirdiği `LoadFrom` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="29899-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="29899-126">Derleme ve yolun basit adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29899-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="29899-127">Ayrıca kullanmaktan kaçınmak için Azaltıcı Etkenler öneren `LoadFrom` bağlamı.</span><span class="sxs-lookup"><span data-stu-id="29899-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="29899-128">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="29899-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="29899-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="29899-129">Example</span></span>  
 <span data-ttu-id="29899-130">Aşağıdaki kod örneği, bu MDA etkinleştirebilirsiniz bir durumu gösterir:</span><span class="sxs-lookup"><span data-stu-id="29899-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="29899-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29899-131">See Also</span></span>  
 [<span data-ttu-id="29899-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="29899-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
