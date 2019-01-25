---
title: MDA Hazırlama
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37351dadf941e3512249dd8a9f433b63065ae1fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626894"
---
# <a name="marshaling-mda"></a><span data-ttu-id="c7c05-102">MDA Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c7c05-102">marshaling MDA</span></span>
<span data-ttu-id="c7c05-103">`marshaling` Yönetilen hata ayıklama Yardımcısı (MDA), bir yöntem parametresi veya bir yapının bir alan için bilgi sıralama yukarı CLR kümeleri kullanırken etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c7c05-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="c7c05-104">Bu MDA, JIT olarak derlenmiş derlemelerde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="c7c05-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c7c05-105">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="c7c05-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="c7c05-106">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c7c05-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c7c05-107">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c7c05-107">Output</span></span>  
 <span data-ttu-id="c7c05-108">MDA, yönetilen ve yönetilmeyen bağlamları ve yapısı veya türünü içeren bir yöntem parametresi veya alan türünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c7c05-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="c7c05-109">Bir alan için çıktının bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c7c05-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="c7c05-110">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c7c05-110">Configuration</span></span>  
 <span data-ttu-id="c7c05-111">MDA yapılandırma, bildirilen sıralama bilgileri dahil olan alan veya yöntem adları göre filtrelemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="c7c05-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="c7c05-112">Aşağıdaki örnek kullanımını gösterir `methodFilter`, `fieldFilter`, ve `match` filtre belirtmek için öğeleri.</span><span class="sxs-lookup"><span data-stu-id="c7c05-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="c7c05-113">Ayar `name` özniteliği için bir yıldız işareti (\*), her şeyi eşleşir.</span><span class="sxs-lookup"><span data-stu-id="c7c05-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7c05-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7c05-114">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c7c05-115">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c7c05-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c7c05-116">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c7c05-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
