---
title: "MDA Hazırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3f92e849798f03702ca9a5eab3120067a651c999
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-mda"></a><span data-ttu-id="ffe87-102">MDA Hazırlama</span><span class="sxs-lookup"><span data-stu-id="ffe87-102">marshaling MDA</span></span>
<span data-ttu-id="ffe87-103">`marshaling` Yönetilen hata ayıklama Yardımcısı (MDA) CLR yöntem parametresi ya da bir yapı bir alan için bilgi sıralama yukarı ayarladığında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ffe87-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="ffe87-104">Bu MDA JIT derlenmiş derlemeler için çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="ffe87-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="ffe87-105">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="ffe87-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="ffe87-106">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ffe87-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="ffe87-107">Çıkış</span><span class="sxs-lookup"><span data-stu-id="ffe87-107">Output</span></span>  
 <span data-ttu-id="ffe87-108">MDA yönetilen ve yönetilmeyen bağlamları ve yapısı veya türünü içeren yöntemi parametresi veya alan türünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ffe87-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="ffe87-109">Bir alan için çıktının bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ffe87-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="ffe87-110">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ffe87-110">Configuration</span></span>  
 <span data-ttu-id="ffe87-111">MDA yapılandırma söz konusu alan veya yöntem adlarını temel alarak bildirilen sıralama bilgileri filtre etmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffe87-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="ffe87-112">Aşağıdaki örnek kullanımı gösterilmiştir `methodFilter`, `fieldFilter`, ve `match` öğeleri filtreleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="ffe87-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="ffe87-113">Ayarı `name` özniteliği için bir yıldız işareti (*) her şeyi eşleşir.</span><span class="sxs-lookup"><span data-stu-id="ffe87-113">Setting the `name` attribute to an asterisk (*) will match everything.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffe87-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffe87-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="ffe87-115">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="ffe87-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="ffe87-116">Birlikte çalışma hazırlama</span><span class="sxs-lookup"><span data-stu-id="ffe87-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
