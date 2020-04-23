---
title: "Nasıl yapılır: COM'dan .NET Türlerine Başvurma"
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
ms.openlocfilehash: 0223cb25b933cc84af49aa86d90259fdf1fd3efc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124168"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="97428-102">Nasıl yapılır: COM'dan .NET Türlerine Başvurma</span><span class="sxs-lookup"><span data-stu-id="97428-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="97428-103">İstemci ve sunucu kodunun bakış noktasından, COM ile .NET Framework arasındaki farklar büyük ölçüde görünmez değildir.</span><span class="sxs-lookup"><span data-stu-id="97428-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="97428-104">Microsoft Visual Basic istemcileri, nesne yöntemleri ve söz dizimi, Özellikler ve alanları tamamen başka bir COM nesnesi gibi sunan nesne tarayıcısında bir .NET nesnesini görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="97428-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="97428-105">Bir tür kitaplığını içeri aktarma işlemi, C++ istemcileri için biraz daha karmaşıktır, ancak meta verileri bir COM tür kitaplığına aktarmak için aynı araçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97428-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="97428-106">Yönetilmeyen bir C++ istemcisinden .NET nesne üyelerine başvurmak için **#import** YÖNERGESI ile TLB dosyasına (Tlbexp. exe ile üretildi) başvurun.</span><span class="sxs-lookup"><span data-stu-id="97428-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="97428-107">C++ ' dan bir tür kitaplığına başvurulduğunda, **raw_interfaces_only** seçeneğini belirtmeniz veya tanımları, mscorlib. tlb temel sınıf kitaplığında içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="97428-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="97428-108">Bir kitaplığı içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="97428-108">To import a library</span></span>  
  
- <span data-ttu-id="97428-109">**#İmport** yönergesinde **raw_interfaces_only** seçeneğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="97428-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="97428-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="97428-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="97428-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="97428-111">-or-</span></span>  
  
- <span data-ttu-id="97428-112">Mscorlib. tlb için bir #import yönergesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="97428-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="97428-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="97428-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97428-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97428-114">See also</span></span>

- [<span data-ttu-id="97428-115">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="97428-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="97428-116">Derlemeleri COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="97428-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="97428-117">[.NET nesnesi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="97428-117">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="97428-118">[COM erişimi için uygulama dağıtma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="97428-118">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
