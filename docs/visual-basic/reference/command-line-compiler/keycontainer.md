---
title: -keycontainer
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b433182a502761fb3840ed2003cc50e053fb072a
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-keycontainer"></a><span data-ttu-id="6535e-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="6535e-102">-keycontainer</span></span>
<span data-ttu-id="6535e-103">Bir derleme tanımlayıcı bir ad vermek bir anahtar çifti için bir anahtar kapsayıcı adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6535e-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6535e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6535e-104">Syntax</span></span>  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="6535e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6535e-105">Arguments</span></span>  
  
|<span data-ttu-id="6535e-106">Terim</span><span class="sxs-lookup"><span data-stu-id="6535e-106">Term</span></span>|<span data-ttu-id="6535e-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="6535e-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="6535e-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6535e-108">Required.</span></span> <span data-ttu-id="6535e-109">Anahtar içeren kapsayıcı dosyası.</span><span class="sxs-lookup"><span data-stu-id="6535e-109">Container file that contains the key.</span></span> <span data-ttu-id="6535e-110">Dosya adını tırnak işaretleri içine alın ("") adı boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="6535e-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6535e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6535e-111">Remarks</span></span>  
 <span data-ttu-id="6535e-112">Derleyici, bir ortak anahtar derleme bildirimine ekleyerek ve son derlemeyi özel anahtarıyla açarak paylaşılabilir bir bileşen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6535e-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="6535e-113">Bir anahtar dosyası oluşturmak için şunu yazın `sn -k``file` komut satırında.</span><span class="sxs-lookup"><span data-stu-id="6535e-113">To generate a key file, type `sn -k``file` at the command line.</span></span> <span data-ttu-id="6535e-114">`-i` Seçeneği anahtar çiftini bir kapsayıcıya yükler.</span><span class="sxs-lookup"><span data-stu-id="6535e-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="6535e-115">Daha fazla bilgi için bkz: [Sn.exe (tanımlayıcı ad aracı)][Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="6535e-115">For more information, see [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="6535e-116">İle derleme yaparsanız `-target:module`, anahtar dosyasının adı modülde tutulur ve bir derleme derlediğinizde oluşturduğunuz derlemesini birleştirilmiş [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="6535e-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="6535e-117">Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyNameAttribute>) herhangi bir Microsoft Ara dili (MSIL) modülü için kaynak kodundaki.</span><span class="sxs-lookup"><span data-stu-id="6535e-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="6535e-118">Derleyici ile şifreleme bilgilerinizi geçirebilirsiniz [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="6535e-118">You can also pass your encryption information to the compiler with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="6535e-119">Kullanım [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) kısmen imzalı bir derleme istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="6535e-119">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="6535e-120">Bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) derleme imzalama hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="6535e-120">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6535e-121">`-keycontainer` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6535e-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6535e-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="6535e-122">Example</span></span>  
 <span data-ttu-id="6535e-123">Aşağıdaki kod kaynak dosyasını derler `Input.vb` ve bir anahtar kapsayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6535e-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6535e-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6535e-124">See Also</span></span>  
 [<span data-ttu-id="6535e-125">Derlemeler ve Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="6535e-125">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="6535e-126">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="6535e-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="6535e-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="6535e-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="6535e-128">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="6535e-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
