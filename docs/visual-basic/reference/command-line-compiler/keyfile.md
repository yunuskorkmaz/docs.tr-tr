---
title: /keyfile
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0be7d230f16750395aaceb3c94539546716b8fd
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="keyfile"></a><span data-ttu-id="b3971-102">/keyfile</span><span class="sxs-lookup"><span data-stu-id="b3971-102">/keyfile</span></span>
<span data-ttu-id="b3971-103">Bir anahtar ya da bir derleme tanımlayıcı bir ad vermek için anahtar çiftini içeren dosyayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3971-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3971-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3971-104">Syntax</span></span>  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="b3971-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b3971-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="b3971-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b3971-106">Required.</span></span> <span data-ttu-id="b3971-107">Anahtarı içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="b3971-107">File that contains the key.</span></span> <span data-ttu-id="b3971-108">Dosya adı boşluk içeriyorsa adı tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="b3971-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3971-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3971-109">Remarks</span></span>  
 <span data-ttu-id="b3971-110">Derleyici derleme bildirimine ortak anahtar ekler ve ardından son derlemeyi özel anahtarıyla imzalar.</span><span class="sxs-lookup"><span data-stu-id="b3971-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="b3971-111">Bir anahtar dosyası oluşturmak için şunu yazın `sn -k file` komut satırında.</span><span class="sxs-lookup"><span data-stu-id="b3971-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="b3971-112">Daha fazla bilgi için bkz: [Sn.exe (tanımlayıcı ad aracı)][Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="b3971-112">For more information, see [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="b3971-113">İle derleme yaparsanız `/target:module`, anahtar dosyasının adı modülde tutulur ve bir derleme derlediğinizde oluşturduğunuz derlemesini birleştirilmiş [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="b3971-113">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="b3971-114">Derleyici ile şifreleme bilgilerinizi geçirebilirsiniz [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="b3971-114">You can also pass your encryption information to the compiler with [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="b3971-115">Kullanım [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) kısmen imzalı bir derleme istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="b3971-115">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="b3971-116">Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyFileAttribute>) herhangi bir Microsoft Ara dile modülü için kaynak kodundaki.</span><span class="sxs-lookup"><span data-stu-id="b3971-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="b3971-117">İçinde her ikisi de case `/keyfile` ve [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) belirtilir (komut satırı seçeneğini veya göre özel öznitelik) aynı derlemede derleyici önce anahtar kapsayıcısı dener.</span><span class="sxs-lookup"><span data-stu-id="b3971-117">In case both `/keyfile` and [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="b3971-118">Bu başarılı olursa, derleme anahtar kapsayıcısı içindeki bilgilerle imzalanır.</span><span class="sxs-lookup"><span data-stu-id="b3971-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="b3971-119">Derleyici anahtar kapsayıcısını bulamazsa ile belirtilen dosyayı çalışır `/keyfile`.</span><span class="sxs-lookup"><span data-stu-id="b3971-119">If the compiler does not find the key container, it tries the file specified with `/keyfile`.</span></span> <span data-ttu-id="b3971-120">Bu başarılı olursa, derleme anahtar dosyası içindeki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısında yüklenir (benzer şekilde `sn -i`) sonraki derlemede anahtar kapsayıcısı geçerli olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b3971-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="b3971-121">Bir anahtar dosyası yalnızca ortak anahtar içerebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b3971-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="b3971-122">Bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) derleme imzalama hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="b3971-122">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3971-123">`/keyfile` Seçeneği içinde kullanılabilir değil [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] geliştirme ortamı; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3971-123">The `/keyfile` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3971-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3971-124">Example</span></span>  
 <span data-ttu-id="b3971-125">Aşağıdaki kod kaynak dosyasını derler `Input.vb` ve bir anahtar dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3971-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3971-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3971-126">See Also</span></span>  
 [<span data-ttu-id="b3971-127">Derlemeler ve Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="b3971-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="b3971-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b3971-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b3971-129">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3971-129">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="b3971-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b3971-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
