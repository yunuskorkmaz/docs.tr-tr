---
title: "Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bdf39da2a597d75479a2a3ed3d60132a0f7e7def
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="9b452-102">Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9b452-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>
<span data-ttu-id="9b452-103">Birincil birlikte çalışma derlemesi oluşturmak için iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="9b452-103">There are two ways to generate a primary interop assembly:</span></span>  
  
-   <span data-ttu-id="9b452-104">Kullanarak [tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b452-104">Using the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
     <span data-ttu-id="9b452-105">Birincil birlikte çalışma derlemeleri üretmek için en kolay yolu kullanmaktır [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="9b452-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="9b452-106">Tlbimp.exe aşağıdaki güvenlik önlemleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="9b452-106">Tlbimp.exe provides the following safeguards:</span></span>  
  
    -   <span data-ttu-id="9b452-107">Tüm iç içe geçmiş tür kitaplığı başvuruları yeni birlikte çalışma derlemeleri oluşturmadan önce diğer kayıtlı birincil birlikte çalışma derlemeleri denetler.</span><span class="sxs-lookup"><span data-stu-id="9b452-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>  
  
    -   <span data-ttu-id="9b452-108">Kapsayıcı ya da birincil birlikte çalışma derlemesi güçlü bir ad vermek için dosya adı belirtmezseniz, birincil birlikte çalışma derlemesi yaymak üzere başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9b452-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>  
  
    -   <span data-ttu-id="9b452-109">Birincil birlikte çalışma derlemesi bağımlı derlemeleri başvurular atlarsanız yaymak üzere başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9b452-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>  
  
    -   <span data-ttu-id="9b452-110">Birincil birlikte çalışma derlemeleri olmayan bağımlı derlemeleri başvurular eklerseniz, birincil birlikte çalışma derlemesi yaymak üzere başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9b452-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>  
  
-   <span data-ttu-id="9b452-111">Birincil birlikte çalışma derlemeleri ile ortak dil belirtimi (CLS), C# gibi uyumlu bir dil kullanarak kaynak kodunda el ile oluşturma.</span><span class="sxs-lookup"><span data-stu-id="9b452-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="9b452-112">Bu yaklaşım, bir tür kitaplığı kullanılamıyor yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9b452-112">This approach is useful when a type library is unavailable.</span></span>  
  
 <span data-ttu-id="9b452-113">Derlemeyi tanımlayıcı adla imzalamak için şifreleme anahtar çiftinin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b452-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="9b452-114">Ayrıntılar için bkz [bir anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="9b452-114">For details, see [Creating A Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="9b452-115">Tlbimp.exe kullanarak birincil birlikte çalışma derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9b452-115">To generate a primary interop assembly using Tlbimp.exe</span></span>  
  
1.  <span data-ttu-id="9b452-116">Komut isteminde, şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="9b452-116">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="9b452-117">**Tlbimp** *tlbfile***/birincil/keyfile:** *filename* **/out:** *assemblyname* </span><span class="sxs-lookup"><span data-stu-id="9b452-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>  
  
     <span data-ttu-id="9b452-118">Bu komutta *tlbfile* COM tür kitaplığı içeren bir dosya *filename* kapsayıcı veya anahtar çiftini içeren dosya adıdır ve *assemblyname* olduğu tanımlayıcı ad ile imzalamak için derleme adı.</span><span class="sxs-lookup"><span data-stu-id="9b452-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>  
  
 <span data-ttu-id="9b452-119">Birincil birlikte çalışma derlemeleri yalnızca diğer birincil birlikte çalışma derlemeleri başvuruda bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="9b452-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="9b452-120">Derlemenizi bir üçüncü taraf COM tür kitaplığından türleri başvuruyorsa, birincil birlikte çalışma derlemenizi oluşturmadan önce birincil birlikte çalışma derlemesi yayımcıdan edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b452-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="9b452-121">Yayımcı varsa, başvuru birincil birlikte çalışma derlemesi oluşturmadan birincil birlikte çalışma için bir derleme bağımlı tür kitaplığı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b452-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>  
  
 <span data-ttu-id="9b452-122">Bağımlı bir birincil birlikte çalışma derlemesi özgün tür kitaplığı farklı bir sürüm numarası geçerli dizinde yüklendiğinde bulunabilirlik değil.</span><span class="sxs-lookup"><span data-stu-id="9b452-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="9b452-123">Windows Kayıt Defteri'nde bağımlı birincil birlikte çalışma derlemesini kaydetme veya kullanmak **/reference** seçeneği Tlbimp.exe bağımlı DLL bulduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9b452-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>  
  
 <span data-ttu-id="9b452-124">Tür kitaplığı birden fazla sürümünü de kayabilir.</span><span class="sxs-lookup"><span data-stu-id="9b452-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="9b452-125">Yönergeler için bkz: [nasıl yapılır: kaydırma birden çok sürümleri, tür kitaplıklarının](https://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9b452-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b452-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b452-126">Example</span></span>  
 <span data-ttu-id="9b452-127">Aşağıdaki örnek COM tür kitaplığı içeri aktarır `LibUtil.tlb` ve derleme imzalar `LibUtil.dll` anahtar dosyası kullanarak tanımlayıcı bir ad ile `CompanyA.snk`.</span><span class="sxs-lookup"><span data-stu-id="9b452-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="9b452-128">Belirli bir ad alanı adı kaldırarak bu örnek varsayılan ad alanı üretir `LibUtil`.</span><span class="sxs-lookup"><span data-stu-id="9b452-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 <span data-ttu-id="9b452-129">Daha açıklayıcı bir ad için (kullanarak *SatıcıAdı*. *LibraryName* kılavuz adlandırma), aşağıdaki örnekte varsayılan derleme dosya adı ve ad alanı adı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9b452-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 <span data-ttu-id="9b452-130">Aşağıdaki örnek alır `MyLib.tlb`, hangi başvuruları `CompanyA.LibUtil.dll`, ve derleme imzalar `CompanyB.MyLib.dll` anahtar dosyası kullanarak tanımlayıcı bir ad ile `CompanyB.snk`.</span><span class="sxs-lookup"><span data-stu-id="9b452-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="9b452-131">Ad alanı `CompanyB.MyLib`, varsayılan ad alanı adı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9b452-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b452-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b452-132">See Also</span></span>  
 [<span data-ttu-id="9b452-133">Nasıl yapılır: Birincil Birlikte Çalışma Bütünleştirilmiş Kodlarını Kaydetme</span><span class="sxs-lookup"><span data-stu-id="9b452-133">How to: Register Primary Interop Assemblies</span></span>](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
