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
ms.openlocfilehash: fead2d4296cfa6fb0195cb4b43f6448c0fc7e6a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970145"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="0d381-102">-keycontainer (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="0d381-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="0d381-103">Şifreleme anahtar kapsayıcısının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d381-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d381-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d381-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="0d381-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="0d381-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="0d381-106">Güçlü ad anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="0d381-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d381-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d381-107">Remarks</span></span>  
 <span data-ttu-id="0d381-108">**-keycontainer** seçeneği kullanıldığında, derleyici sharable bir bileşen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d381-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="0d381-109">Derleyici, belirtilen kapsayıcıdan ortak bir anahtarı montaj bildirimine ekler ve son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="0d381-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="0d381-110">Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın.</span><span class="sxs-lookup"><span data-stu-id="0d381-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="0d381-111">`sn -i`anahtar çiftini bir kapsayıcıya yükler.</span><span class="sxs-lookup"><span data-stu-id="0d381-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="0d381-112">Derleyici CoreCLR'de çalıştığında bu seçenek desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0d381-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="0d381-113">CoreCLR'da montaj yaparken bir derlemeyi imzalamak için [-keyfile](keyfile-compiler-option.md) seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d381-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="0d381-114">[-target:module](./target-module-compiler-option.md)ile derlerseniz, anahtar dosyasının adı modülde tutulur ve bu modülü [-addmodule](./addmodule-compiler-option.md)ile bir derlemeye eklediğinizde derlemeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="0d381-114">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="0d381-115">Bu seçeneği, herhangi bir Microsoft ara<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>dili (MSIL) modülü için kaynak kodunda özel bir öznitelik ( ) olarak da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d381-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="0d381-116">Şifreleme bilgilerinizi [-keyfile](./keyfile-compiler-option.md)ile derleyiciye de iletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d381-116">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="0d381-117">Ortak anahtarın derleme bildirimine eklenmesini istiyorsanız, ancak derlemenin test edilene kadar imzalanmasını geciktirmek istiyorsanız [-geciktirme işaretini](./delaysign-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d381-117">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="0d381-118">Daha fazla bilgi için [bkz.](../../../standard/assembly/create-use-strong-named.md) [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md)</span><span class="sxs-lookup"><span data-stu-id="0d381-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0d381-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0d381-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="0d381-120">Bu derleyici seçeneği Visual Studio geliştirme ortamında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0d381-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="0d381-121">Bu derleyici seçeneğine programlı <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>olarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d381-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d381-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d381-122">See also</span></span>

- [<span data-ttu-id="0d381-123">C# Derleyici -keyfile seçeneği</span><span class="sxs-lookup"><span data-stu-id="0d381-123">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="0d381-124">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0d381-124">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="0d381-125">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="0d381-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
