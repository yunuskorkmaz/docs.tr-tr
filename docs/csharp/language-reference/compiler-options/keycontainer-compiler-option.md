---
description: -keycontainer (C# derleyici seçenekleri)
title: -keycontainer (C# derleyici seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 93ee5cd755a4fd6918d2a5825b63151a201a8f6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152474"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="afc90-103">-keycontainer (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="afc90-103">-keycontainer (C# Compiler Options)</span></span>

<span data-ttu-id="afc90-104">Şifreleme anahtarı kapsayıcısının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="afc90-104">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afc90-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="afc90-105">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="afc90-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="afc90-106">Arguments</span></span>  

 `string`  
 <span data-ttu-id="afc90-107">Tanımlayıcı ad anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="afc90-107">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afc90-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afc90-108">Remarks</span></span>  

 <span data-ttu-id="afc90-109">**-Keycontainer** seçeneği kullanıldığında, derleyici paylaşılabilir bir bileşen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="afc90-109">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="afc90-110">Derleyici, belirtilen kapsayıcıdan derleme bildirimine ortak bir anahtar ekler ve son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="afc90-110">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="afc90-111">Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın.</span><span class="sxs-lookup"><span data-stu-id="afc90-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="afc90-112">`sn -i` anahtar çiftini bir kapsayıcıya kurar.</span><span class="sxs-lookup"><span data-stu-id="afc90-112">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="afc90-113">Derleyici CoreCLR üzerinde çalıştırıldığında bu seçenek desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="afc90-113">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="afc90-114">CoreCLR üzerinde oluşturma sırasında bir derlemeyi imzalamak için [-keyfile](keyfile-compiler-option.md) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="afc90-114">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="afc90-115">[-Target: Module](./target-module-compiler-option.md)ile derleme yaparsanız, anahtar dosyasının adı modülde tutulur ve bu modülü [-addmodule](./addmodule-compiler-option.md)ile bir derlemede derlerken derlemeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="afc90-115">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="afc90-116">Bu seçeneği, <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType> herhangi bir Microsoft ara dili (MSIL) modülünün kaynak kodunda özel bir öznitelik () olarak da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afc90-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="afc90-117">Ayrıca, [-keyfile](./keyfile-compiler-option.md)ile şifreleme bilgilerinizi derleyiciye geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afc90-117">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="afc90-118">Ortak anahtarın derleme bildirimine eklenmesini istiyorsanız, ancak test edilene kadar derlemeyi imzalamak istiyorsanız [-delaysign](./delaysign-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="afc90-118">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="afc90-119">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) ve [bir derlemeyi imzalamayı geciktirme](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="afc90-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="afc90-120">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="afc90-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="afc90-121">Bu derleyici seçeneği, Visual Studio geliştirme ortamında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="afc90-121">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="afc90-122">Bu derleyici seçeneğine aracılığıyla programlı bir şekilde erişebilirsiniz <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A> .</span><span class="sxs-lookup"><span data-stu-id="afc90-122">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc90-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afc90-123">See also</span></span>

- [<span data-ttu-id="afc90-124">C# Derleyici-anahtar seçeneği</span><span class="sxs-lookup"><span data-stu-id="afc90-124">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="afc90-125">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="afc90-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="afc90-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="afc90-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
