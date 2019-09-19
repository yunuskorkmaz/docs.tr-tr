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
ms.openlocfilehash: fcdff732afce90f725f4730f0054296e389ada1b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051794"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="477a5-102">Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="477a5-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="477a5-103">[Tür kitaplığı alma programı (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) , com tür kitaplığı 'nda bulunan coclass 'ları ve arabirimleri meta verilere dönüştüren bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="477a5-103">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="477a5-104">Bu araç otomatik olarak tür bilgileri için birlikte çalışma derlemesi ve ad alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="477a5-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="477a5-105">Bir sınıfın meta verileri kullanılabilir olduktan sonra, yönetilen istemciler COM türünde örnekler oluşturabilir ve kendi yöntemlerini, tıpkı bir .NET örneğinde olduğu gibi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="477a5-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="477a5-106">Tlbimp. exe bir tür kitaplığının tamamını aynı anda meta verilere dönüştürür ve tür kitaplığında tanımlanan türlerin bir alt kümesi için tür bilgisi üretmez.</span><span class="sxs-lookup"><span data-stu-id="477a5-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="477a5-107">Bir tür kitaplığından birlikte çalışma derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="477a5-107">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="477a5-108">Aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="477a5-108">Use the following command:</span></span>  
  
     <span data-ttu-id="477a5-109">**Tlbimp** *tür-kitaplık-dosya* \<></span><span class="sxs-lookup"><span data-stu-id="477a5-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="477a5-110">**/Out:** anahtarını eklemek, krelib. dll gibi değiştirilmiş bir ada sahip bir birlikte çalışma derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="477a5-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="477a5-111">Birlikte çalışma derleme adının değiştirilmesi, özgün COM DLL 'sinden ayırt etmenize yardımcı olabilir ve yinelenen adlara sahip olmadan oluşabilecek sorunları önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="477a5-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="477a5-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="477a5-112">Example</span></span>  
 <span data-ttu-id="477a5-113">Aşağıdaki komut, `Loanlib` ad alanındaki krelib. dll derlemesini üretir.</span><span class="sxs-lookup"><span data-stu-id="477a5-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="477a5-114">Aşağıdaki komut, değiştirilmiş bir ada (Krelib. dll) sahip bir birlikte çalışma derlemesi üretir.</span><span class="sxs-lookup"><span data-stu-id="477a5-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="477a5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="477a5-115">See also</span></span>

- [<span data-ttu-id="477a5-116">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="477a5-116">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="477a5-117">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="477a5-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
