---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266748"
---
# <a name="-keyfile"></a><span data-ttu-id="6e2e9-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="6e2e9-102">-keyfile</span></span>
<span data-ttu-id="6e2e9-103">Derlemeye tanımlayıcı ad vermek için bir anahtar veya anahtar çifti içeren bir dosya belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e2e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e2e9-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="6e2e9-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="6e2e9-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="6e2e9-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-106">Required.</span></span> <span data-ttu-id="6e2e9-107">Anahtarı içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-107">File that contains the key.</span></span> <span data-ttu-id="6e2e9-108">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e2e9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e2e9-109">Remarks</span></span>  
 <span data-ttu-id="6e2e9-110">Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="6e2e9-111">Anahtar dosyası oluşturmak için komut satırına yazın `sn -k file` .</span><span class="sxs-lookup"><span data-stu-id="6e2e9-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="6e2e9-112">Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="6e2e9-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="6e2e9-113">İle `-target:module`derlerseniz, anahtar dosyasının adı modülde tutulur ve [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="6e2e9-114">Ayrıca, şifreleme bilgilerinizi [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)ile derleyiciye geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="6e2e9-115">Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="6e2e9-116">Bu seçeneği, herhangi bir Microsoft ara dil modülünün kaynak kodunda<xref:System.Reflection.AssemblyKeyFileAttribute>özel bir öznitelik () olarak da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="6e2e9-117">Aynı derlemede hem `-keyfile` hem de [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) belirtildiğinde (komut satırı seçeneği ya da özel öznitelik tarafından), derleyici ilk olarak anahtar kapsayıcısını dener.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="6e2e9-118">Bu başarılı olursa, derleme anahtar kapsayıcısındaki bilgilerle imzalanır.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="6e2e9-119">Derleyici anahtar kapsayıcısını bulamazsa, ile `-keyfile`belirtilen dosyayı dener.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="6e2e9-120">Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri, sonraki derlemede anahtar kapsayıcısının geçerli olacağı şekilde anahtar kapsayıcısına yüklenir (buna benzer `sn -i`).</span><span class="sxs-lookup"><span data-stu-id="6e2e9-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="6e2e9-121">Anahtar dosyasının yalnızca ortak anahtar içerebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="6e2e9-122">Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="6e2e9-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e2e9-123">Bu `-keyfile` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="6e2e9-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e2e9-124">Example</span></span>

<span data-ttu-id="6e2e9-125">Aşağıdaki kod, kaynak dosyayı `Input.vb` derler ve bir anahtar dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="6e2e9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e2e9-126">See also</span></span>

- [<span data-ttu-id="6e2e9-127">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="6e2e9-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="6e2e9-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="6e2e9-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6e2e9-129">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e2e9-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="6e2e9-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="6e2e9-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
