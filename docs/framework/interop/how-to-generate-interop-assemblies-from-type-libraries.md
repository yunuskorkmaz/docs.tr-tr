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
ms.openlocfilehash: aea23daff28b50678b9fa7902857fc302494c4a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387737"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="be994-102">Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="be994-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="be994-103">[Tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) meta veriler için bir COM türü kitaplığında bulunan arabirimleri ve coclass'ları dönüştüren bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="be994-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="be994-104">Bu araç birlikte çalışma derlemesi ve ad alanı türü bilgileri için otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be994-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="be994-105">Meta veri sınıfının kullanılabilir olduktan sonra yönetilen istemciler COM türünün örneklerini oluşturmak ve yalnızca bir .NET örneği gibi kendi yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="be994-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="be994-106">Tlbimp.exe tüm tür kitaplığı meta verileri aynı anda dönüştürür ve bir tür kitaplığı'nda tanımlanan türlerden bir alt tür bilgileri oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="be994-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="be994-107">Birlikte çalışma bütünleştirilmiş bir tür kitaplığından oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="be994-107">To generate an interop assembly from a type library</span></span>  
  
1.  <span data-ttu-id="be994-108">Aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="be994-108">Use the following command:</span></span>  
  
     <span data-ttu-id="be994-109">**Tlbimp** \< *türü kitaplık dosyası*></span><span class="sxs-lookup"><span data-stu-id="be994-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="be994-110">Ekleme **/out:** anahtar LOANLib.dll gibi değiştirilmiş bir ad ile birlikte çalışma derleme üretir.</span><span class="sxs-lookup"><span data-stu-id="be994-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="be994-111">Birlikte çalışma derleme adının değiştirilmesi, özgün COM DLL'den ayırt etmek ve yinelenen adları olan ortaya çıkabilecek sorunları önlemek yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="be994-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be994-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="be994-112">Example</span></span>  
 <span data-ttu-id="be994-113">Aşağıdaki komutu Loanlib.dll derlemede üreten `Loanlib` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="be994-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.dll  
```  
  
 <span data-ttu-id="be994-114">Aşağıdaki komutu değiştirilmiş bir ad (LOANLib.dll) ile birlikte çalışma derleme üretir.</span><span class="sxs-lookup"><span data-stu-id="be994-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="be994-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be994-115">See Also</span></span>  
 [<span data-ttu-id="be994-116">Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="be994-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="be994-117">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="be994-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
