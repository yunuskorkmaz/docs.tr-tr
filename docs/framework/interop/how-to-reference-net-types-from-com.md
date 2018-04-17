---
title: "Nasıl yapılır: COM'dan .NET Türlerine Başvurma"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ac4308230f29067f358a45fd7f882abe6e41b96
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="55c16-102">Nasıl yapılır: COM'dan .NET Türlerine Başvurma</span><span class="sxs-lookup"><span data-stu-id="55c16-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="55c16-103">İstemci ve sunucu kodu point of görünümünü COM ve .NET Framework arasındaki farklar büyük ölçüde görünmez.</span><span class="sxs-lookup"><span data-stu-id="55c16-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="55c16-104">Microsoft Visual Basic istemcileri .NET nesnesi sözdizimi, özelliklerini ve nesne yöntemleri sunar ve tam olarak herhangi bir COM nesnesi gibi alanları nesne tarayıcısında görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55c16-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="55c16-105">Tür kitaplığını içeri aktarma işlemi C++ istemcileri için biraz daha karmaşık olsa meta verileri için bir COM tür kitaplığı dışarı aktarmak için aynı araçlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="55c16-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="55c16-106">Yönetilmeyen bir C++ istemciden .NET nesne üyeleri başvurmak için ile (Tlbexp.exe ile üretilen) TLB dosya başvuru **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="55c16-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="55c16-107">C++ içinden bir tür kitaplığı başvuru yapıldığında, ya da belirtmeniz gerekir **raw_interfaces_only** seçeneğini veya Mscorlib.tlb temel sınıf kitaplığı'nda tanımını içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="55c16-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="55c16-108">Bir kitaplık içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="55c16-108">To import a library</span></span>  
  
-   <span data-ttu-id="55c16-109">Belirtin **raw_interfaces_only** seçeneğini **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="55c16-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="55c16-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="55c16-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="55c16-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="55c16-111">-or-</span></span>  
  
-   <span data-ttu-id="55c16-112">#İmport yönergesi için Mscorlib.tlb içerir.</span><span class="sxs-lookup"><span data-stu-id="55c16-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="55c16-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="55c16-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="55c16-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55c16-114">See Also</span></span>  
 [<span data-ttu-id="55c16-115">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="55c16-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="55c16-116">Bütünleştirilmiş Kodları COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="55c16-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)  
 <span data-ttu-id="55c16-117">[Bir .NET nesnesini çağırma](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55c16-117">[Calling a .NET Object](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span></span>  
 <span data-ttu-id="55c16-118">[COM erişim için bir uygulama dağıtma](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55c16-118">[Deploying an Application for COM Access](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span></span>
