---
title: -keycontainer (C# Derleyici Seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 5a7b378cad7a1df9249fcbefa28bb9aa9a6a3da4
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472574"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="fbafe-102">-keycontainer (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="fbafe-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="fbafe-103">Şifreleme anahtarı kapsayıcısının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbafe-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbafe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fbafe-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="fbafe-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fbafe-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="fbafe-106">Güçlü ad anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="fbafe-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbafe-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fbafe-107">Remarks</span></span>  
 <span data-ttu-id="fbafe-108">Zaman **- keycontainer** seçeneği kullanıldığında, derleyici paylaşılabilir bir bileşen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fbafe-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="fbafe-109">Derleyici bir ortak anahtar belirtilmiş kapsayıcıdan derleme bildirimine ekler ve son derlemeyi özel anahtarıyla imzalar.</span><span class="sxs-lookup"><span data-stu-id="fbafe-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="fbafe-110">Bir anahtar dosyası oluşturmak için şunu yazın `sn -k file` komut satırında.</span><span class="sxs-lookup"><span data-stu-id="fbafe-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="fbafe-111">`sn -i` anahtar çiftini bir kapsayıcıya yükler.</span><span class="sxs-lookup"><span data-stu-id="fbafe-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="fbafe-112">Derleyici CoreCLR üzerinde çalıştığında, bu seçeneği desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="fbafe-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="fbafe-113">Üzerinde CoreCLR oluştururken derlemeyi imzalamak için kullanın [- keyfile](keyfile-compiler-option.md) seçeneği.</span><span class="sxs-lookup"><span data-stu-id="fbafe-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="fbafe-114">İle derleme yaparsanız [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), anahtar dosyasının adı modülde tutulur ve bir derleme halinde bu modül derlediğinizde derlemeye birleştirilmiş [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="fbafe-114">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="fbafe-115">Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) herhangi bir Microsoft Ara dili (MSIL) modülü için kaynak kodundaki.</span><span class="sxs-lookup"><span data-stu-id="fbafe-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="fbafe-116">Derleyici ile şifreleme bilgilerinizi geçirebilirsiniz [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="fbafe-116">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="fbafe-117">Kullanım [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) ortak anahtar derleme bildirimi eklenmesini istediğiniz ancak test edilmiştir kadar derleme imzalamayı geciktirme istersiniz.</span><span class="sxs-lookup"><span data-stu-id="fbafe-117">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="fbafe-118">Daha fazla bilgi için bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [Gecikmeli bir derleme imzalama](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="fbafe-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fbafe-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fbafe-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="fbafe-120">Bu derleyici seçeneği Visual Studio geliştirme ortamında kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="fbafe-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="fbafe-121">Bu derleyici seçeneği ile program aracılığıyla erişebilirsiniz <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="fbafe-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbafe-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbafe-122">See Also</span></span>  
 <span data-ttu-id="fbafe-123">[C# Derleyici - keyfile seçeneği](keyfile-compiler-option.md) [C# Derleyici Seçenekleri](index.md)</span><span class="sxs-lookup"><span data-stu-id="fbafe-123">[C# Compiler -keyfile option](keyfile-compiler-option.md) [C# Compiler Options](index.md)</span></span>  
 [<span data-ttu-id="fbafe-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="fbafe-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
