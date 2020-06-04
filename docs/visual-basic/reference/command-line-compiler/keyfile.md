---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 3f476f6b6db1a788002a938eb5ae4bbbed7a5dae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408581"
---
# <a name="-keyfile"></a><span data-ttu-id="7104b-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="7104b-102">-keyfile</span></span>
<span data-ttu-id="7104b-103">Derlemeye tanımlayıcı ad vermek için bir anahtar veya anahtar çifti içeren bir dosya belirtir.</span><span class="sxs-lookup"><span data-stu-id="7104b-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7104b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7104b-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="7104b-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="7104b-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="7104b-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7104b-106">Required.</span></span> <span data-ttu-id="7104b-107">Anahtarı içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="7104b-107">File that contains the key.</span></span> <span data-ttu-id="7104b-108">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="7104b-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7104b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7104b-109">Remarks</span></span>  
 <span data-ttu-id="7104b-110">Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="7104b-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="7104b-111">Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın.</span><span class="sxs-lookup"><span data-stu-id="7104b-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="7104b-112">Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="7104b-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="7104b-113">İle derlerseniz `-target:module` , anahtar dosyasının adı modülde tutulur ve [-addmodule](addmodule.md)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="7104b-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="7104b-114">Ayrıca, şifreleme bilgilerinizi [-keycontainer](keycontainer.md)ile derleyiciye geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7104b-114">You can also pass your encryption information to the compiler with [-keycontainer](keycontainer.md).</span></span> <span data-ttu-id="7104b-115">Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](delaysign.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7104b-115">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="7104b-116">Bu seçeneği <xref:System.Reflection.AssemblyKeyFileAttribute> , herhangi bir Microsoft ara dil modülünün kaynak kodunda özel bir öznitelik () olarak da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7104b-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="7104b-117">Aynı derlemede hem hem de `-keyfile` [-keycontainer](keycontainer.md) belirtildiğinde (komut satırı seçeneği ya da özel öznitelik tarafından), derleyici ilk olarak anahtar kapsayıcısını dener.</span><span class="sxs-lookup"><span data-stu-id="7104b-117">In case both `-keyfile` and [-keycontainer](keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="7104b-118">Bu başarılı olursa, derleme anahtar kapsayıcısındaki bilgilerle imzalanır.</span><span class="sxs-lookup"><span data-stu-id="7104b-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="7104b-119">Derleyici anahtar kapsayıcısını bulamazsa, ile belirtilen dosyayı dener `-keyfile` .</span><span class="sxs-lookup"><span data-stu-id="7104b-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="7104b-120">Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri, `sn -i` sonraki derlemede anahtar kapsayıcısının geçerli olacağı şekilde anahtar kapsayıcısına yüklenir (buna benzer).</span><span class="sxs-lookup"><span data-stu-id="7104b-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="7104b-121">Anahtar dosyasının yalnızca ortak anahtar içerebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7104b-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="7104b-122">Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="7104b-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7104b-123">`-keyfile`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7104b-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="7104b-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="7104b-124">Example</span></span>

<span data-ttu-id="7104b-125">Aşağıdaki kod, kaynak dosyayı derler `Input.vb` ve bir anahtar dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="7104b-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="7104b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7104b-126">See also</span></span>

- [<span data-ttu-id="7104b-127">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="7104b-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="7104b-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="7104b-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7104b-129">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7104b-129">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="7104b-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="7104b-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
