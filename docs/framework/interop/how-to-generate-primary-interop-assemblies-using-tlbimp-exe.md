---
title: 'Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
ms.openlocfilehash: e46295b89b042452cb6e303302a8b88d68d58426
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123919"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="f7f5f-102">Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7f5f-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>

<span data-ttu-id="f7f5f-103">Birincil birlikte çalışma derlemesi oluşturmak için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="f7f5f-103">There are two ways to generate a primary interop assembly:</span></span>

- <span data-ttu-id="f7f5f-104">Windows SDK tarafından sunulan [tür kitaplığı alma programı (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) kullanma.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-104">Using the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) provided by the Windows SDK.</span></span>

  <span data-ttu-id="f7f5f-105">Birincil birlikte çalışma derlemelerini oluşturmanın en kolay yolu [Tlbimp. exe ' yi (tür kitaplığı alma)](../tools/tlbimp-exe-type-library-importer.md)kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="f7f5f-106">Tlbimp. exe aşağıdaki korumaları sağlar:</span><span class="sxs-lookup"><span data-stu-id="f7f5f-106">Tlbimp.exe provides the following safeguards:</span></span>

  - <span data-ttu-id="f7f5f-107">Tüm iç içe geçmiş tür kitaplığı başvuruları için yeni birlikte çalışma derlemeleri oluşturmadan önce diğer kayıtlı birincil birlikte çalışma derlemelerini denetler.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>

  - <span data-ttu-id="f7f5f-108">Birincil birlikte çalışma derlemesine tanımlayıcı bir ad vermek için kapsayıcı veya dosya adı belirtmezseniz, birincil birlikte çalışma derlemesini yayma başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>

  - <span data-ttu-id="f7f5f-109">Bağımlı derlemelere yönelik başvuruları atlarsanız, birincil birlikte çalışma derlemesi yayılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>

  - <span data-ttu-id="f7f5f-110">Birincil birlikte çalışma derlemeleri olmayan bağımlı derlemelere başvurular eklerseniz, birincil birlikte çalışma derlemesi yayılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>

- <span data-ttu-id="f7f5f-111">Ortak dil belirtimi (CLS) ile uyumlu bir dil kullanarak kaynak kodunda el ile birincil birlikte çalışma derlemeleri oluşturma (örneğin,) C#.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="f7f5f-112">Bu yaklaşım, bir tür kitaplığı kullanılamadığında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-112">This approach is useful when a type library is unavailable.</span></span>

<span data-ttu-id="f7f5f-113">Derlemeyi güçlü bir adla imzalamak için bir şifreleme anahtarı çiftiniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="f7f5f-114">Ayrıntılar için bkz. [anahtar çifti oluşturma](../../standard/assembly/create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="f7f5f-114">For details, see [Creating A Key Pair](../../standard/assembly/create-public-private-key-pair.md).</span></span>

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="f7f5f-115">Tlbimp. exe kullanarak birincil birlikte çalışma derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f7f5f-115">To generate a primary interop assembly using Tlbimp.exe</span></span>

1. <span data-ttu-id="f7f5f-116">Komut isteminde, şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="f7f5f-116">At the command prompt, type:</span></span>

    <span data-ttu-id="f7f5f-117">**Tlbimp** *tlbdosya*  **/birincil/anahtar adı:** *filename* **/Out:** *AssemblyName*</span><span class="sxs-lookup"><span data-stu-id="f7f5f-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>

    <span data-ttu-id="f7f5f-118">Bu komutta, *tlbdosya* com tür kitaplığını içeren dosyadır, *filename* anahtar çiftini içeren kapsayıcının veya dosyanın adı ve *AssemblyName* ise tanımlayıcı bir adla imzalanacak derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>

<span data-ttu-id="f7f5f-119">Birincil birlikte çalışma derlemeleri yalnızca diğer birincil birlikte çalışma derlemelerine başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="f7f5f-120">Derlemeniz bir üçüncü taraf COM tür kitaplığından türlere başvuruyorsa, birincil birlikte çalışma derlemenizi oluşturabilmeniz için önce yayımcıdan bir birincil birlikte çalışma derlemesi edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="f7f5f-121">Yayımcı kullanıyorsanız, başvuran birincil birlikte çalışma derlemesini oluşturmadan önce bağımlı tür kitaplığı için bir birincil birlikte çalışma derlemesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>

<span data-ttu-id="f7f5f-122">Özgün tür kitaplığından farklı bir sürüm numarasına sahip bağımlı bir birincil birlikte çalışma derlemesi, geçerli dizine yüklendiğinde keşfedilemez.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="f7f5f-123">Tlbimp. exe ' nın bağımlı DLL 'yi bulmasını sağlamak için, bağımlı birincil birlikte çalışma derlemesini Windows kayıt defterine kaydetmeniz veya **/Reference** seçeneğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>

<span data-ttu-id="f7f5f-124">Ayrıca, bir tür kitaplığının birden çok sürümünü de kaydırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="f7f5f-125">Yönergeler için bkz. [nasıl yapılır: tür kitaplıklarının birden çok sürümünü sarın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f7f5f-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="f7f5f-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7f5f-126">Example</span></span>

<span data-ttu-id="f7f5f-127">Aşağıdaki örnek, COM tür kitaplığı `LibUtil.tlb` içeri aktarır ve derleme `LibUtil.dll` anahtar dosya `CompanyA.snk`kullanarak tanımlayıcı bir adla imzalar.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="f7f5f-128">Belirli bir ad alanı adını atlayarak Bu örnek, `LibUtil`varsayılan ad alanını üretir.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

<span data-ttu-id="f7f5f-129">Daha açıklayıcı bir ad ( *VendorName*kullanarak). *LibraryName* adlandırma Kılavuzu) aşağıdaki örnek, varsayılan derleme dosya adı ve ad alanı adını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

<span data-ttu-id="f7f5f-130">Aşağıdaki örnek, `CompanyA.LibUtil.dll`başvuran `MyLib.tlb`içeri aktarır ve derleme `CompanyB.MyLib.dll` anahtar dosya `CompanyB.snk`kullanarak tanımlayıcı bir adla imzalar.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="f7f5f-131">Ad alanı `CompanyB.MyLib`, varsayılan ad alanı adını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a><span data-ttu-id="f7f5f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7f5f-132">See also</span></span>

- [<span data-ttu-id="f7f5f-133">Nasıl yapılır: Birincil Birlikte Çalışma Bütünleştirilmiş Kodlarını Kaydetme</span><span class="sxs-lookup"><span data-stu-id="f7f5f-133">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)
