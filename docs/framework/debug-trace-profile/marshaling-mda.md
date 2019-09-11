---
title: MDA Sıralama
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b1a1607e96ad9953a409d79fd265ced994cece2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854140"
---
# <a name="marshaling-mda"></a><span data-ttu-id="d4634-102">MDA Sıralama</span><span class="sxs-lookup"><span data-stu-id="d4634-102">marshaling MDA</span></span>
<span data-ttu-id="d4634-103">`marshaling` Yönetilen hata ayıklama Yardımcısı (MDA), clr bir yöntem parametresi veya bir yapının alanı için sıralama bilgilerini ayarlarsa etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d4634-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="d4634-104">Bu MDA, JıT derlenmiş derlemeler için çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="d4634-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d4634-105">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="d4634-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="d4634-106">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d4634-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d4634-107">Çıkış</span><span class="sxs-lookup"><span data-stu-id="d4634-107">Output</span></span>  
 <span data-ttu-id="d4634-108">MDA, yönetilen ve yönetilmeyen bağlamlardaki parametre ya da alanın türünü ve türünü içeren yapıyı ya da yöntemi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d4634-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="d4634-109">Bir alan için çıktının bir örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d4634-109">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="d4634-110">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d4634-110">Configuration</span></span>  
 <span data-ttu-id="d4634-111">MDA yapılandırması, bildirilen sıralama bilgilerini ilgili alana veya yöntem adlarına göre filtrelemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="d4634-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="d4634-112">Aşağıdaki örnek `methodFilter`, filtre belirtmek için, `fieldFilter`ve `match` öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4634-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="d4634-113">Özniteliği bir yıldız işareti (\*) olarak ayarlamak her şeyi eşleştirecektir. `name`</span><span class="sxs-lookup"><span data-stu-id="d4634-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4634-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4634-114">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d4634-115">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="d4634-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d4634-116">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="d4634-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
