---
title: "Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf56d33a791dd91614d5ae37e3568ef660696af7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="71d44-102">Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="71d44-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="71d44-103">[Tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) meta veriler için bir COM türü kitaplığında bulunan arabirimleri ve coclass'ları dönüştüren bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="71d44-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="71d44-104">Bu araç birlikte çalışma derlemesi ve ad alanı türü bilgileri için otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71d44-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="71d44-105">Meta veri sınıfının kullanılabilir olduktan sonra yönetilen istemciler COM türünün örneklerini oluşturmak ve yalnızca bir .NET örneği gibi kendi yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="71d44-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="71d44-106">Tlbimp.exe tüm tür kitaplığı meta verileri aynı anda dönüştürür ve bir tür kitaplığı'nda tanımlanan türlerden bir alt tür bilgileri oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="71d44-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="71d44-107">Birlikte çalışma bütünleştirilmiş bir tür kitaplığından oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="71d44-107">To generate an interop assembly from a type library</span></span>  
  
1.  <span data-ttu-id="71d44-108">Aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="71d44-108">Use the following command:</span></span>  
  
     <span data-ttu-id="71d44-109">**Tlbimp** \< *türü kitaplık dosyası*></span><span class="sxs-lookup"><span data-stu-id="71d44-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="71d44-110">Ekleme **/out:** anahtar LOANLib.dll gibi değiştirilmiş bir ad ile birlikte çalışma derleme üretir.</span><span class="sxs-lookup"><span data-stu-id="71d44-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="71d44-111">Birlikte çalışma derleme adının değiştirilmesi, özgün COM DLL'den ayırt etmek ve yinelenen adları olan ortaya çıkabilecek sorunları önlemek yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="71d44-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71d44-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="71d44-112">Example</span></span>  
 <span data-ttu-id="71d44-113">Aşağıdaki komutu Loanlib.dll derlemede üreten `Loanlib` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="71d44-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.dll  
```  
  
 <span data-ttu-id="71d44-114">Aşağıdaki komutu değiştirilmiş bir ad (LOANLib.dll) ile birlikte çalışma derleme üretir.</span><span class="sxs-lookup"><span data-stu-id="71d44-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="71d44-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71d44-115">See Also</span></span>  
 [<span data-ttu-id="71d44-116">Tür kitaplığını derleme olarak içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="71d44-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="71d44-117">COM bileşenlerini .NET Framework'te gösterme</span><span class="sxs-lookup"><span data-stu-id="71d44-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
