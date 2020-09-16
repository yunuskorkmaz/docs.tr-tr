---
title: "Nasıl yapılır: COM'dan .NET Türlerine Başvurma"
description: COM 'dan .NET türlerine başvurun. VB istemcileri, nesne tarayıcısında bir .NET nesnesini görüntüleyebilir, ancak C++ istemcilerinin içeri aktarma yönergesi ile bir TLB dosyasına başvurması gerekir \# .
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
ms.openlocfilehash: fad0a8163bd3d023911fd8554a77f740ac010ee6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547251"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="11c35-104">Nasıl yapılır: COM'dan .NET Türlerine Başvurma</span><span class="sxs-lookup"><span data-stu-id="11c35-104">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="11c35-105">İstemci ve sunucu kodunun bakış noktasından, COM ile .NET Framework arasındaki farklar büyük ölçüde görünmez değildir.</span><span class="sxs-lookup"><span data-stu-id="11c35-105">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="11c35-106">Microsoft Visual Basic istemcileri, nesne yöntemleri ve söz dizimi, Özellikler ve alanları tamamen başka bir COM nesnesi gibi sunan nesne tarayıcısında bir .NET nesnesini görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="11c35-106">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="11c35-107">Bir tür kitaplığını içeri aktarma işlemi, C++ istemcileri için biraz daha karmaşıktır, ancak meta verileri bir COM tür kitaplığına aktarmak için aynı araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11c35-107">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="11c35-108">Yönetilmeyen bir C++ istemcisinden .NET nesne üyelerine başvurmak için, **#import** YÖNERGESI ile TLB dosyasına (Tlbexp.exe ile üretilen) başvurun.</span><span class="sxs-lookup"><span data-stu-id="11c35-108">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="11c35-109">C++ ' dan bir tür kitaplığına başvurulduğunda, **raw_interfaces_only** seçeneğini belirtmeniz veya tanımları, mscorlib. tlb temel sınıf kitaplığında içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="11c35-109">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="11c35-110">Bir kitaplığı içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="11c35-110">To import a library</span></span>  
  
- <span data-ttu-id="11c35-111">**#İmport** yönergesinde **raw_interfaces_only** seçeneğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="11c35-111">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="11c35-112">Örnek:</span><span class="sxs-lookup"><span data-stu-id="11c35-112">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="11c35-113">-veya-</span><span class="sxs-lookup"><span data-stu-id="11c35-113">-or-</span></span>  
  
- <span data-ttu-id="11c35-114">Mscorlib. tlb için bir #import yönergesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11c35-114">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="11c35-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="11c35-115">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="11c35-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11c35-116">See also</span></span>

- [<span data-ttu-id="11c35-117">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="11c35-117">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="11c35-118">Derlemeleri COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="11c35-118">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="11c35-119">[.NET nesnesi çağırma](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="11c35-119">[Calling a .NET Object](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="11c35-120">[COM erişimi için uygulama dağıtma](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="11c35-120">[Deploying an Application for COM Access](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
