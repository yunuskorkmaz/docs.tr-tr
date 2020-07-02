---
title: 'Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma'
description: Tür kitaplıklarından birlikte çalışma derlemeleri oluşturun. Ortak sınıfları ve arabirimleri bir COM tür kitaplığından meta verilere dönüştürmek için tür kitaplığı alma programı (Tlbimp.exe) kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: 6f54875d6aadb1da18cf25a1bec0a0e451f4a24c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619565"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="0d948-104">Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d948-104">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="0d948-105">[Tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) , com tür kitaplığı 'nda bulunan coclass 'ları ve arabirimlerin meta verilere dönüştürüldüğü bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="0d948-105">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="0d948-106">Bu araç otomatik olarak tür bilgileri için birlikte çalışma derlemesi ve ad alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d948-106">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="0d948-107">Bir sınıfın meta verileri kullanılabilir olduktan sonra, yönetilen istemciler COM türünde örnekler oluşturabilir ve kendi yöntemlerini, tıpkı bir .NET örneğinde olduğu gibi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="0d948-107">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="0d948-108">Tlbimp.exe, tüm tür kitaplığını tek seferde meta verilere dönüştürür ve bir tür kitaplığında tanımlanan türlerin bir alt kümesi için tür bilgisi üretemiyor.</span><span class="sxs-lookup"><span data-stu-id="0d948-108">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="0d948-109">Bir tür kitaplığından birlikte çalışma derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0d948-109">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="0d948-110">Aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0d948-110">Use the following command:</span></span>  
  
     <span data-ttu-id="0d948-111">**Tlbimp**\<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="0d948-111">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="0d948-112">**/Out:** anahtarını eklemek, LOANLib.dll gibi değiştirilmiş bir ada sahip bir birlikte çalışma derlemesi üretir.</span><span class="sxs-lookup"><span data-stu-id="0d948-112">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="0d948-113">Birlikte çalışma derleme adının değiştirilmesi, özgün COM DLL 'sinden ayırt etmenize yardımcı olabilir ve yinelenen adlara sahip olmadan oluşabilecek sorunları önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0d948-113">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d948-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d948-114">Example</span></span>  
 <span data-ttu-id="0d948-115">Aşağıdaki komut ad alanında Loanlib.dll derlemesini üretir `Loanlib` .</span><span class="sxs-lookup"><span data-stu-id="0d948-115">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="0d948-116">Aşağıdaki komut, değiştirilmiş bir ada (LOANLib.dll) sahip bir birlikte çalışma derlemesi üretir.</span><span class="sxs-lookup"><span data-stu-id="0d948-116">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d948-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d948-117">See also</span></span>

- [<span data-ttu-id="0d948-118">Tür Kitaplığını Derleme Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="0d948-118">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="0d948-119">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="0d948-119">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
