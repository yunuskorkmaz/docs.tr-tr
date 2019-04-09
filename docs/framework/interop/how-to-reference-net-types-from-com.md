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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e033ba4b3b98367452b355363058adc7f1a5887
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198406"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="8f693-102">Nasıl yapılır: COM'dan .NET Türlerine Başvurma</span><span class="sxs-lookup"><span data-stu-id="8f693-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="8f693-103">Bakış açısıyla, istemci ve sunucu kodu, COM ve .NET Framework arasındaki farklar büyük ölçüde görünmez.</span><span class="sxs-lookup"><span data-stu-id="8f693-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="8f693-104">Microsoft Visual Basic istemciler, bir .NET nesnesini sözdizimi, özelliklerini ve nesne yöntemleri ve tam olarak bunu herhangi bir COM nesnesi gibi alanlar nesne tarayıcısında görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f693-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="8f693-105">Meta veriler için bir COM tür kitaplığı dışarı aktarmak için aynı araçları kullanmanıza rağmen bir tür kitaplığını içeri aktarma işlemi C++ istemciler için biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="8f693-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="8f693-106">.NET nesne üyeleri bir yönetilmeyen C++ istemcisinden başvurmak için ile (Tlbexp.exe ile üretilen) TLB dosyasına başvurmak **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="8f693-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="8f693-107">Tür kitaplığından başvururken C++, ya da belirtmeniz gerekir **raw_interfaces_only** seçeneğini veya Mscorlib.tlb temel sınıf kitaplığı'nda tanımlarını içe aktarın.</span><span class="sxs-lookup"><span data-stu-id="8f693-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="8f693-108">Bir kitaplığı içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="8f693-108">To import a library</span></span>  
  
-   <span data-ttu-id="8f693-109">Belirtin **raw_interfaces_only** seçeneğini **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="8f693-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="8f693-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8f693-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="8f693-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="8f693-111">-or-</span></span>  
  
-   <span data-ttu-id="8f693-112">#İmport yönergesi için Mscorlib.tlb içerir.</span><span class="sxs-lookup"><span data-stu-id="8f693-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="8f693-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8f693-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8f693-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f693-114">See also</span></span>

- [<span data-ttu-id="8f693-115">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="8f693-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="8f693-116">Derlemeleri COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="8f693-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- [<span data-ttu-id="8f693-117">.NET Nesnesini Çağırma</span><span class="sxs-lookup"><span data-stu-id="8f693-117">Calling a .NET Object</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [<span data-ttu-id="8f693-118">COM Erişimi için Bir Uygulamayı Dağıtma</span><span class="sxs-lookup"><span data-stu-id="8f693-118">Deploying an Application for COM Access</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
