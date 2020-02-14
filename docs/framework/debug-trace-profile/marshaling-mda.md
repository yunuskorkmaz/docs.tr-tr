---
title: MDA Sıralama
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: f7bb630d3a1e832cf6bf083ce4cf603034248ceb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217328"
---
# <a name="marshaling-mda"></a><span data-ttu-id="4b527-102">MDA Sıralama</span><span class="sxs-lookup"><span data-stu-id="4b527-102">marshaling MDA</span></span>
<span data-ttu-id="4b527-103">`marshaling` yönetilen hata ayıklama Yardımcısı (MDA), CLR bir yöntem parametresi veya bir yapının alanı için sıralama bilgilerini ayarlarsa etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4b527-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="4b527-104">Bu MDA, JıT derlenmiş derlemeler için çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="4b527-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4b527-105">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="4b527-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="4b527-106">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4b527-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4b527-107">Çıktı</span><span class="sxs-lookup"><span data-stu-id="4b527-107">Output</span></span>  
 <span data-ttu-id="4b527-108">MDA, yönetilen ve yönetilmeyen bağlamlardaki parametre ya da alanın türünü ve türünü içeren yapıyı ya da yöntemi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4b527-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="4b527-109">Bir alan için çıktının bir örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4b527-109">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="4b527-110">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4b527-110">Configuration</span></span>  
 <span data-ttu-id="4b527-111">MDA yapılandırması, bildirilen sıralama bilgilerini ilgili alana veya yöntem adlarına göre filtrelemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="4b527-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="4b527-112">Aşağıdaki örnek, filtreleri belirtmek için `methodFilter`, `fieldFilter`ve `match` öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b527-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="4b527-113">`name` özniteliğini bir yıldız işareti (\*) olarak ayarlamak her şeyi eşleştirecektir.</span><span class="sxs-lookup"><span data-stu-id="4b527-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b527-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b527-114">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="4b527-115">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="4b527-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4b527-116">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="4b527-116">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
