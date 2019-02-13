---
title: 'Nasıl yapılır: COM başvurusu .NET türlerinden'
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
ms.openlocfilehash: c5151d89feccbe68daa5a8de4aa3b75a42511899
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220276"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="25433-102">Nasıl yapılır: COM başvurusu .NET türlerinden</span><span class="sxs-lookup"><span data-stu-id="25433-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="25433-103">Bakış açısıyla, istemci ve sunucu kodu, COM ve .NET Framework arasındaki farklar büyük ölçüde görünmez.</span><span class="sxs-lookup"><span data-stu-id="25433-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="25433-104">Microsoft Visual Basic istemciler, bir .NET nesnesini sözdizimi, özelliklerini ve nesne yöntemleri ve tam olarak bunu herhangi bir COM nesnesi gibi alanlar nesne tarayıcısında görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25433-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="25433-105">Meta veriler için bir COM tür kitaplığı dışarı aktarmak için aynı araçları kullanmanıza rağmen bir tür kitaplığını içeri aktarma işlemi C++ istemciler için biraz daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="25433-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="25433-106">.NET nesne üyeleri bir yönetilmeyen C++ istemcisinden başvurmak için ile (Tlbexp.exe ile üretilen) TLB dosyasına başvurmak **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="25433-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="25433-107">Bir tür kitaplığı C++'tan başvururken ya da belirtmelisiniz **raw_interfaces_only** seçeneğini veya Mscorlib.tlb temel sınıf kitaplığı'nda tanımlarını içe aktarın.</span><span class="sxs-lookup"><span data-stu-id="25433-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="25433-108">Bir kitaplığı içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="25433-108">To import a library</span></span>  
  
-   <span data-ttu-id="25433-109">Belirtin **raw_interfaces_only** seçeneğini **#import** yönergesi.</span><span class="sxs-lookup"><span data-stu-id="25433-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="25433-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="25433-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="25433-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="25433-111">-or-</span></span>  
  
-   <span data-ttu-id="25433-112">#İmport yönergesi için Mscorlib.tlb içerir.</span><span class="sxs-lookup"><span data-stu-id="25433-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="25433-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="25433-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="25433-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25433-114">See also</span></span>
- [<span data-ttu-id="25433-115">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="25433-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="25433-116">Bütünleştirilmiş Kodları COM ile Kaydetme</span><span class="sxs-lookup"><span data-stu-id="25433-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="25433-117">[Bir .NET nesnesini çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="25433-117">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="25433-118">[COM erişimi için bir uygulama dağıtma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="25433-118">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
