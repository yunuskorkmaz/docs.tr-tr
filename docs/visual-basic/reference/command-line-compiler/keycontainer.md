---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: be2ad1416e801398fb513593c7f3828e5488bfaf
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005532"
---
# <a name="-keycontainer"></a><span data-ttu-id="96479-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="96479-102">-keycontainer</span></span>
<span data-ttu-id="96479-103">Bir derlemeye tanımlayıcı ad vermek için bir anahtar çifti için anahtar kapsayıcısı adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="96479-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96479-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96479-104">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="96479-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="96479-105">Arguments</span></span>  
  
|<span data-ttu-id="96479-106">Terim</span><span class="sxs-lookup"><span data-stu-id="96479-106">Term</span></span>|<span data-ttu-id="96479-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="96479-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="96479-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="96479-108">Required.</span></span> <span data-ttu-id="96479-109">Anahtarı içeren kapsayıcı dosyası.</span><span class="sxs-lookup"><span data-stu-id="96479-109">Container file that contains the key.</span></span> <span data-ttu-id="96479-110">Ad bir boşluk içeriyorsa, dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="96479-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96479-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96479-111">Remarks</span></span>  
 <span data-ttu-id="96479-112">Derleyici, derleme bildirimine ortak anahtar ekleyerek ve son derlemeyi özel anahtarla imzalayarak paylaşılabilir bileşeni oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96479-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="96479-113">Anahtar dosyası oluşturmak için komut satırına `sn -k file` yazın.</span><span class="sxs-lookup"><span data-stu-id="96479-113">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="96479-114">@No__t-0 seçeneği, anahtar çiftini bir kapsayıcıya kurar.</span><span class="sxs-lookup"><span data-stu-id="96479-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="96479-115">Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="96479-115">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="96479-116">@No__t-0 ile derlerseniz, anahtar dosyasının adı modülde tutulur ve [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="96479-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="96479-117">Bu seçeneği, herhangi bir Microsoft ara dili (MSIL) modülünün kaynak kodunda özel bir öznitelik (<xref:System.Reflection.AssemblyKeyNameAttribute>) olarak da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96479-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="96479-118">Ayrıca, [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)ile şifreleme bilgilerinizi derleyiciye geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96479-118">You can also pass your encryption information to the compiler with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="96479-119">Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="96479-119">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="96479-120">Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="96479-120">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96479-121">@No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="96479-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96479-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="96479-122">Example</span></span>  
 <span data-ttu-id="96479-123">Aşağıdaki kod `Input.vb` kaynak dosyasını derler ve bir anahtar kapsayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="96479-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="96479-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96479-124">See also</span></span>

- [<span data-ttu-id="96479-125">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="96479-125">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="96479-126">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="96479-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="96479-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="96479-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="96479-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="96479-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
