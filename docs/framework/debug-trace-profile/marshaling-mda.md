---
title: MDA Sıralama
description: CLR bir yöntem parametresi veya bir yapı alanı için sıralama bilgilerini ayarlarsa çağrılan, yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: 77811c526d1770b91b14aa1199dfc7b3177e6c59
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051161"
---
# <a name="marshaling-mda"></a><span data-ttu-id="d53c4-103">MDA Sıralama</span><span class="sxs-lookup"><span data-stu-id="d53c4-103">marshaling MDA</span></span>
<span data-ttu-id="d53c4-104">`marshaling`Yönetilen hata ayıklama Yardımcısı (MDA), clr bir yöntem parametresi veya bir yapının alanı için sıralama bilgilerini ayarlarsa etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d53c4-104">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="d53c4-105">Bu MDA, JıT derlenmiş derlemeler için çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="d53c4-105">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="d53c4-106">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="d53c4-106">Effect on the Runtime</span></span>  
 <span data-ttu-id="d53c4-107">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d53c4-107">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="d53c4-108">Çıktı</span><span class="sxs-lookup"><span data-stu-id="d53c4-108">Output</span></span>  
 <span data-ttu-id="d53c4-109">MDA, yönetilen ve yönetilmeyen bağlamlardaki parametre ya da alanın türünü ve türünü içeren yapıyı ya da yöntemi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d53c4-109">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="d53c4-110">Bir alan için çıktının bir örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d53c4-110">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="d53c4-111">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d53c4-111">Configuration</span></span>  
 <span data-ttu-id="d53c4-112">MDA yapılandırması, bildirilen sıralama bilgilerini ilgili alana veya yöntem adlarına göre filtrelemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="d53c4-112">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="d53c4-113">Aşağıdaki örnek `methodFilter` , `fieldFilter` `match` filtre belirtmek için, ve öğelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d53c4-113">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="d53c4-114">`name`Özniteliği bir yıldız işareti () olarak ayarlamak \* her şeyi eşleştirecektir.</span><span class="sxs-lookup"><span data-stu-id="d53c4-114">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d53c4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d53c4-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="d53c4-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="d53c4-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d53c4-117">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="d53c4-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
