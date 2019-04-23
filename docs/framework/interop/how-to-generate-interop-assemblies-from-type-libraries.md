---
title: 'Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a3ee82a9091f0caeee010ec79632ce703efb589
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338845"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="21f42-102">Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="21f42-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="21f42-103">[Tür kitaplığı alma programı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) meta verileri için bir COM tür kitaplığında bulunan arabirimleri ve coclass'ları dönüştürür bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="21f42-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="21f42-104">Bu araç bir birlikte çalışma derlemesi ve tür bilgisi için ad alanı otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21f42-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="21f42-105">Bir sınıfın meta verileri kullanıma sunulduktan sonra yönetilen istemcilerin COM tür örnekleri oluşturma ve bir .NET örneği sanki olarak kendi yöntemlerini çağırmaya.</span><span class="sxs-lookup"><span data-stu-id="21f42-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="21f42-106">Tlbimp.exe tüm tür kitaplığında tek seferde meta verisine dönüştürür ve tür kitaplığında tanımlanan türlerin bir alt kümesi için tür bilgisi oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="21f42-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="21f42-107">Tür kitaplığından bir birlikte çalışma derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="21f42-107">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="21f42-108">Aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="21f42-108">Use the following command:</span></span>  
  
     <span data-ttu-id="21f42-109">**Tlbimp** \< *tür kitaplığı dosyası*></span><span class="sxs-lookup"><span data-stu-id="21f42-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="21f42-110">Ekleme **/out:** anahtar LOANLib.dll gibi değiştirilmiş bir ad ile birlikte çalışma derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21f42-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="21f42-111">Birlikte çalışma bütünleştirilmiş kod adı değiştirme yinelenen adları, oluşabilecek sorunları önlemek ve özgün COM DLL dosyasından ayırt yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="21f42-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21f42-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="21f42-112">Example</span></span>  
 <span data-ttu-id="21f42-113">Aşağıdaki komutu Loanlib.dll derlemesinde oluşturur `Loanlib` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="21f42-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="21f42-114">Aşağıdaki komut değiştirilen bir ad (LOANLib.dll) ile birlikte çalışma derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21f42-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="21f42-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21f42-115">See also</span></span>

- [<span data-ttu-id="21f42-116">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="21f42-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="21f42-117">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="21f42-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
