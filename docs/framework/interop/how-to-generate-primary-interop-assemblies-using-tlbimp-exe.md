---
title: 'Nasıl yapılır: Tlbimp.exe kullanarak birincil birlikte çalışma derlemeleri oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1136dd3220b189d60b4972410ce0ce6657d07cd
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218989"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="a08c4-102">Nasıl yapılır: Tlbimp.exe kullanarak birincil birlikte çalışma derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="a08c4-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>
<span data-ttu-id="a08c4-103">Birincil birlikte çalışma derlemesi oluşturmak için iki yolunuz vardır:</span><span class="sxs-lookup"><span data-stu-id="a08c4-103">There are two ways to generate a primary interop assembly:</span></span>  
  
-   <span data-ttu-id="a08c4-104">Kullanarak [tür kitaplığı alma programı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a08c4-104">Using the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
     <span data-ttu-id="a08c4-105">Birincil birlikte çalışma derlemeleri oluşturmak için en kolay yolu [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="a08c4-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="a08c4-106">Tlbimp.exe aşağıdaki güvenlik önlemleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="a08c4-106">Tlbimp.exe provides the following safeguards:</span></span>  
  
    -   <span data-ttu-id="a08c4-107">Tüm iç içe geçmiş tür kitaplığı başvurularını için yeni birlikte çalışma derlemeleri oluşturmadan önce diğer kayıtlı birincil birlikte çalışma derlemelerini denetler.</span><span class="sxs-lookup"><span data-stu-id="a08c4-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>  
  
    -   <span data-ttu-id="a08c4-108">Kapsayıcı ya da birincil birlikte çalışma derlemesini bir katı ad vermek için dosya adı belirtmezseniz, birincil birlikte çalışma derlemesi yaymak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a08c4-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>  
  
    -   <span data-ttu-id="a08c4-109">Bağımlı derlemelerin başvurularını atlarsanız, birincil birlikte çalışma derlemesi yaymak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a08c4-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>  
  
    -   <span data-ttu-id="a08c4-110">Birincil birlikte çalışma derlemelerini olmayan bağımlı derlemelerin başvurularını eklerseniz, birincil birlikte çalışma derlemesi yaymak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a08c4-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>  
  
-   <span data-ttu-id="a08c4-111">Kaynak kodunda el ile oluşturma gibi ortak dil belirtimi (CLS) ile uyumlu bir dil kullanarak birincil birlikte çalışma derlemelerini C#.</span><span class="sxs-lookup"><span data-stu-id="a08c4-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="a08c4-112">Bu yaklaşım, bir tür kitaplığı kullanılamadığında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a08c4-112">This approach is useful when a type library is unavailable.</span></span>  
  
 <span data-ttu-id="a08c4-113">Derlemeyi tanımlayıcı bir adla imzalamak için bir şifreleme anahtarı çiftiniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a08c4-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="a08c4-114">Ayrıntılar için bkz [bir anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="a08c4-114">For details, see [Creating A Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="a08c4-115">Tlbimp.exe kullanarak birincil birlikte çalışma derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a08c4-115">To generate a primary interop assembly using Tlbimp.exe</span></span>  
  
1.  <span data-ttu-id="a08c4-116">Komut isteminde, şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="a08c4-116">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="a08c4-117">**Tlbimp** *tlbfile\*\*\*/birincil/keyfile:*\* *filename* **/out:** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="a08c4-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>  
  
     <span data-ttu-id="a08c4-118">Bu komutta *tlbfile* COM tür kitaplığı içeren bir dosya *filename* kapsayıcısı veya anahtar çiftini içeren dosyanın adı ve *assemblyname* olduğu tanımlayıcı ad ile işaretlenecek derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="a08c4-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>  
  
 <span data-ttu-id="a08c4-119">Birincil birlikte çalışma derlemeleri, yalnızca diğer birincil birlikte çalışma derlemelerini başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a08c4-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="a08c4-120">Derlemenizi üçüncü taraf COM tür kitaplığından türleri başvuruyorsa, birincil birlikte çalışma bütünleştirilmiş kodunuzda oluşturmadan önce bir birincil birlikte çalışma derlemesi yayımcıdan edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a08c4-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="a08c4-121">Yayımcı ise başvuru birincil birlikte çalışma bütünleştirilmiş kodu oluşturuluyor önce birincil birlikte çalışma derlemesi bağımlı tür kitaplığı için oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a08c4-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>  
  
 <span data-ttu-id="a08c4-122">Bağımlı bir birincil birlikte çalışma derlemesi, özgün tür kitaplığına farklı bir sürüm numarası geçerli dizinde yüklendiğinde bulunabilirlik değil.</span><span class="sxs-lookup"><span data-stu-id="a08c4-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="a08c4-123">Windows kayıt defterinde bağımlı birincil birlikte çalışma derlemesi veya kullanın **/reference** Tlbimp.exe bağımlı DLL bulur emin olmak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a08c4-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>  
  
 <span data-ttu-id="a08c4-124">Ayrıca, birden çok tür kitaplığı sürümünü sarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a08c4-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="a08c4-125">Yönergeler için [nasıl yapılır: Birden çok tür kitaplığı sürümünü sarmalama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a08c4-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a08c4-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="a08c4-126">Example</span></span>  
 <span data-ttu-id="a08c4-127">Aşağıdaki örnek, COM tür kitaplığı içeri aktarır `LibUtil.tlb` ve derlemeyi imzalar `LibUtil.dll` anahtar dosyasını kullanarak bir katı adla `CompanyA.snk`.</span><span class="sxs-lookup"><span data-stu-id="a08c4-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="a08c4-128">Bu örnek varsayılan ad üretir belirli ad alanı adı gt;(yok) `LibUtil`.</span><span class="sxs-lookup"><span data-stu-id="a08c4-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 <span data-ttu-id="a08c4-129">Daha açıklayıcı bir ad için (kullanarak *SatıcıAdı*. *LibraryName* kılavuz adlandırma), aşağıdaki örnekte varsayılan derleme dosya adı ve ad alanı adını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a08c4-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 <span data-ttu-id="a08c4-130">Aşağıdaki örnek alır `MyLib.tlb`, hangi başvurular `CompanyA.LibUtil.dll`, ve derlemeyi imzalar `CompanyB.MyLib.dll` anahtar dosyasını kullanarak bir katı adla `CompanyB.snk`.</span><span class="sxs-lookup"><span data-stu-id="a08c4-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="a08c4-131">Ad alanı `CompanyB.MyLib`, varsayılan ad alanı adını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a08c4-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="a08c4-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a08c4-132">See also</span></span>
- [<span data-ttu-id="a08c4-133">Nasıl yapılır: Birincil birlikte çalışma derlemelerini kaydetme</span><span class="sxs-lookup"><span data-stu-id="a08c4-133">How to: Register Primary Interop Assemblies</span></span>](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
