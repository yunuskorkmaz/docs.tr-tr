---
description: -keyfile (C# derleyici seçenekleri)
title: -keyfile (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 5af40da18895d47933cb809d710e31a40f14513b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152435"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="5f426-103">-keyfile (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5f426-103">-keyfile (C# Compiler Options)</span></span>

<span data-ttu-id="5f426-104">Şifreleme anahtarını içeren dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f426-104">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f426-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5f426-105">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="5f426-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="5f426-106">Arguments</span></span>  
  
|<span data-ttu-id="5f426-107">Terim</span><span class="sxs-lookup"><span data-stu-id="5f426-107">Term</span></span>|<span data-ttu-id="5f426-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="5f426-108">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="5f426-109">Tanımlayıcı ad anahtarını içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="5f426-109">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f426-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f426-110">Remarks</span></span>  

 <span data-ttu-id="5f426-111">Bu seçenek kullanıldığında, derleyici belirtilen dosyadan ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="5f426-111">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="5f426-112">Anahtar dosyası oluşturmak için komut satırına sn-k yazın `file` .</span><span class="sxs-lookup"><span data-stu-id="5f426-112">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="5f426-113">**-Target: Module**ile derleme yaparsanız, anahtar dosyasının adı modülde tutulur ve [-addmodule](./addmodule-compiler-option.md)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="5f426-113">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="5f426-114">Ayrıca, şifreleme bilgilerinizi [-keycontainer](./keycontainer-compiler-option.md)ile derleyiciye geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f426-114">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="5f426-115">Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](./delaysign-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f426-115">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="5f426-116">Aynı derlemede hem-keyfile hem de-keycontainer belirtildiğinde (komut satırı seçeneği veya özel öznitelik tarafından), derleyici ilk olarak anahtar kapsayıcısını dener.</span><span class="sxs-lookup"><span data-stu-id="5f426-116">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="5f426-117">Bu başarılı olursa, derleme anahtar kapsayıcısındaki bilgilerle imzalanır.</span><span class="sxs-lookup"><span data-stu-id="5f426-117">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="5f426-118">Derleyici anahtar kapsayıcısını bulamazsa,-keyfile ile belirtilen dosyayı dener.</span><span class="sxs-lookup"><span data-stu-id="5f426-118">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="5f426-119">Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri, sonraki derlemede anahtar kapsayıcısının geçerli olacağı şekilde anahtar kapsayıcısına (sn-ı ' ye benzer) yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5f426-119">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="5f426-120">Anahtar dosyasının yalnızca ortak anahtar içerebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5f426-120">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="5f426-121">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) ve [bir derlemeyi imzalamayı geciktirme](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="5f426-121">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5f426-122">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5f426-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5f426-123">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="5f426-123">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="5f426-124">**İmzalama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5f426-124">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="5f426-125">**Tanımlayıcı ad seçin anahtar dosyası** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5f426-125">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="5f426-126">Bu derleyici seçeneğine aracılığıyla programlı bir şekilde erişebilirsiniz <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A> .</span><span class="sxs-lookup"><span data-stu-id="5f426-126">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f426-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f426-127">See also</span></span>

- [<span data-ttu-id="5f426-128">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5f426-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5f426-129">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="5f426-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
