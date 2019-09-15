---
title: -keycontainer (C# derleyici seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: fead2d4296cfa6fb0195cb4b43f6448c0fc7e6a9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970145"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="c8e2e-102">-keycontainer (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c8e2e-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="c8e2e-103">Şifreleme anahtarı kapsayıcısının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e2e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8e2e-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="c8e2e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c8e2e-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="c8e2e-106">Tanımlayıcı ad anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8e2e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8e2e-107">Remarks</span></span>  
 <span data-ttu-id="c8e2e-108">**-Keycontainer** seçeneği kullanıldığında, derleyici paylaşılabilir bir bileşen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="c8e2e-109">Derleyici, belirtilen kapsayıcıdan derleme bildirimine ortak bir anahtar ekler ve son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="c8e2e-110">Anahtar dosyası oluşturmak için komut satırına yazın `sn -k file` .</span><span class="sxs-lookup"><span data-stu-id="c8e2e-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="c8e2e-111">`sn -i`anahtar çiftini bir kapsayıcıya kurar.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="c8e2e-112">Derleyici CoreCLR üzerinde çalıştırıldığında bu seçenek desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="c8e2e-113">CoreCLR üzerinde oluşturma sırasında bir derlemeyi imzalamak için [-keyfile](keyfile-compiler-option.md) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="c8e2e-114">[-Target: Module](./target-module-compiler-option.md)ile derleme yaparsanız, anahtar dosyasının adı modülde tutulur ve bu modülü [-addmodule](./addmodule-compiler-option.md)ile bir derlemede derlerken derlemeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-114">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="c8e2e-115">Bu seçeneği, herhangi bir Microsoft ara dili (MSIL)<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>modülünün kaynak kodunda özel bir öznitelik () olarak da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="c8e2e-116">Ayrıca, [-keyfile](./keyfile-compiler-option.md)ile şifreleme bilgilerinizi derleyiciye geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-116">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="c8e2e-117">Ortak anahtarın derleme bildirimine eklenmesini istiyorsanız, ancak test edilene kadar derlemeyi imzalamak istiyorsanız [-delaysign](./delaysign-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-117">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="c8e2e-118">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) ve [bir derlemeyi imzalamayı geciktirme](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="c8e2e-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c8e2e-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c8e2e-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="c8e2e-120">Bu derleyici seçeneği, Visual Studio geliştirme ortamında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="c8e2e-121">Bu derleyici seçeneğine <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>aracılığıyla programlı bir şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e2e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8e2e-122">See also</span></span>

- [<span data-ttu-id="c8e2e-123">C#Derleyici-anahtar seçeneği</span><span class="sxs-lookup"><span data-stu-id="c8e2e-123">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="c8e2e-124">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c8e2e-124">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="c8e2e-125">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="c8e2e-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
