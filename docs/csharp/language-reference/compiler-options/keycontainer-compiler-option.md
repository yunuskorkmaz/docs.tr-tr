---
title: -keycontaıner (C# Derleyici Seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: cf51bccc98f04c38149ec821b7064a4844d7e804
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302783"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="5098a-102">-keycontaıner (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5098a-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="5098a-103">Şifreleme anahtar kapsayıcısı adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5098a-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5098a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5098a-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="5098a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5098a-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="5098a-106">Tanımlayıcı ad anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="5098a-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5098a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5098a-107">Remarks</span></span>  
 <span data-ttu-id="5098a-108">Zaman **- keycontaıner** seçeneği kullanıldığında, derleyici paylaşılabilir bir bileşen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5098a-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="5098a-109">Derleyici, bir ortak anahtar belirtilen kapsayıcısından derleme bildirimine ekler ve son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="5098a-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="5098a-110">Bir anahtar dosyası oluşturmak için şunu yazın `sn -k file` komut satırına.</span><span class="sxs-lookup"><span data-stu-id="5098a-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="5098a-111">`sn -i` bir kapsayıcıya anahtar çifti yükler.</span><span class="sxs-lookup"><span data-stu-id="5098a-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="5098a-112">CoreCLR derleyici çalıştığında, bu seçeneği desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5098a-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="5098a-113">Coreclr'de derlerken bir derlemeyi imzalamak için kullanmak [- keyfile](keyfile-compiler-option.md) seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5098a-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="5098a-114">Derleme yaparsanız [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), anahtar dosyasının adını modülde tutulur ve sahip bir derleme içine bu modülü derlerken bütünleştirilmiş kod içine dahil [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5098a-114">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="5098a-115">Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) herhangi bir Microsoft Ara dili (MSIL) modülü için kaynak kodunda.</span><span class="sxs-lookup"><span data-stu-id="5098a-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="5098a-116">Derleyici ile şifreleme bilgilerinizi de geçirebilirsiniz [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5098a-116">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="5098a-117">Kullanım [- delaysıgn](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) ortak anahtarı derleme bildirimine eklenmesini istediğiniz ancak edilmiş olan kadar derlemeyi imzalamayı geciktirme istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="5098a-117">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="5098a-118">Daha fazla bilgi için [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="5098a-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5098a-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5098a-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5098a-120">Bu derleyici seçeneğini Visual Studio geliştirme ortamında kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="5098a-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="5098a-121">Bu derleyici seçeneği ile program aracılığıyla erişebileceğiniz <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="5098a-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5098a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5098a-122">See also</span></span>

- [<span data-ttu-id="5098a-123">C# derleyicisi - keyfıle seçeneği</span><span class="sxs-lookup"><span data-stu-id="5098a-123">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="5098a-124">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5098a-124">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="5098a-125">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="5098a-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
