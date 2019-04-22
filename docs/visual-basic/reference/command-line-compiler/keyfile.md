---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: c13f34c23cad9c909c2c5bd3447f1a8fa53f9b4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833339"
---
# <a name="-keyfile"></a><span data-ttu-id="dd003-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="dd003-102">-keyfile</span></span>
<span data-ttu-id="dd003-103">Bir anahtar veya bir derlemeyi bir katı ad vermek için anahtar çifti içeren bir dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd003-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd003-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd003-104">Syntax</span></span>  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="dd003-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dd003-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="dd003-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="dd003-106">Required.</span></span> <span data-ttu-id="dd003-107">Anahtarı içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="dd003-107">File that contains the key.</span></span> <span data-ttu-id="dd003-108">Dosya adı boşluk içeriyorsa adı tırnak içine alın. ("").</span><span class="sxs-lookup"><span data-stu-id="dd003-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd003-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd003-109">Remarks</span></span>  
 <span data-ttu-id="dd003-110">Derleyici ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="dd003-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="dd003-111">Bir anahtar dosyası oluşturmak için şunu yazın `sn -k file` komut satırına.</span><span class="sxs-lookup"><span data-stu-id="dd003-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="dd003-112">Daha fazla bilgi için [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="dd003-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="dd003-113">Derleme yaparsanız `-target:module`, anahtar dosyasının adını modülünde tutulan ve bir derleme ile derleme yaparken, oluşturulan bütünleştirilmiş dahil [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="dd003-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="dd003-114">Derleyici ile şifreleme bilgilerinizi de geçirebilirsiniz [- keycontaıner](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="dd003-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="dd003-115">Kullanım [- delaysıgn](../../../visual-basic/reference/command-line-compiler/delaysign.md) kısmen imzalı bir derleme istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="dd003-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="dd003-116">Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyFileAttribute>) herhangi bir Microsoft Ara dili modülü için kaynak kodunda.</span><span class="sxs-lookup"><span data-stu-id="dd003-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="dd003-117">İçinde her ikisi de case `-keyfile` ve [- keycontaıner](../../../visual-basic/reference/command-line-compiler/keycontainer.md) belirtilirse (komut satırı seçeneği veya özel öznitelik tarafından) aynı derlemede derleyici ilk anahtar kapsayıcısı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="dd003-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="dd003-118">Bu başarılı olursa derleme anahtar kapsayıcısındaki bilgilerle imzalanır.</span><span class="sxs-lookup"><span data-stu-id="dd003-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="dd003-119">Derleyicinin anahtar kapsayıcısını bulamazsa, ile belirtilen dosyayı çalışır `-keyfile`.</span><span class="sxs-lookup"><span data-stu-id="dd003-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="dd003-120">Bu başarılı olursa, derleme anahtar dosyası içindeki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısının içine yüklenir (benzer şekilde `sn -i`) ve böylece sonraki derlemede, anahtar kapsayıcısı geçerli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="dd003-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="dd003-121">Bir anahtar dosyası yalnızca ortak anahtar içerebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dd003-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="dd003-122">Bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) derleme imzalama hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="dd003-122">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd003-123">`-keyfile` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd003-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd003-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd003-124">Example</span></span>  
 <span data-ttu-id="dd003-125">Aşağıdaki kod, kaynak dosyasını derler `Input.vb` ve anahtar dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd003-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd003-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd003-126">See also</span></span>

- [<span data-ttu-id="dd003-127">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="dd003-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="dd003-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="dd003-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="dd003-129">-başvuru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd003-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="dd003-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="dd003-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
