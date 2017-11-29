---
title: "-keycontainer (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0292ff38b1d03f5960a20858fbb9c42a6aff1f43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="keycontainer-c-compiler-options"></a><span data-ttu-id="7d6b9-102">/keycontainer (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="7d6b9-102">/keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="7d6b9-103">Şifreleme anahtarı kapsayıcısının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d6b9-104">Syntax</span></span>  
  
```console  
/keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d6b9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7d6b9-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="7d6b9-106">Güçlü ad anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d6b9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d6b9-107">Remarks</span></span>  
 <span data-ttu-id="7d6b9-108">Zaman **/keycontainer** seçeneği kullanıldığında, bir ortak anahtar belirtilmiş kapsayıcıdan derleme bildirimine ekleme ve özel anahtarla son derleme imzalama tarafından paylaşılabilir bir bileşen derleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-108">When the **/keycontainer** option is used, the compiler creates a sharable component by inserting a public key from the specified container into the assembly manifest and signing the final assembly with the private key.</span></span> <span data-ttu-id="7d6b9-109">Bir anahtar dosyası oluşturmak için sn -k yazın `file` komut satırında.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-109">To generate a key file, type sn -k `file` at the command line.</span></span> <span data-ttu-id="7d6b9-110">sn -i anahtar çiftini bir kapsayıcıya yükler.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-110">sn -i installs the key pair into a container.</span></span>  
  
 <span data-ttu-id="7d6b9-111">İle derleme yaparsanız [/target: Module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), anahtar dosyasının adı modülde tutulur ve bir derleme halinde bu modül derlediğinizde derlemeye birleştirilmiş [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7d6b9-111">If you compile with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="7d6b9-112">Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) herhangi bir Microsoft Ara dili (MSIL) modülü için kaynak kodundaki.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-112">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="7d6b9-113">Derleyici ile şifreleme bilgilerinizi geçirebilirsiniz [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7d6b9-113">You can also pass your encryption information to the compiler with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="7d6b9-114">Kullanım [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) ortak anahtar derleme bildirimi eklenmesini istediğiniz ancak test edilmiştir kadar derleme imzalamayı geciktirme istersiniz.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-114">Use [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="7d6b9-115">Daha fazla bilgi için bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [Gecikmeli bir derleme imzalama](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="7d6b9-115">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7d6b9-116">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7d6b9-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="7d6b9-117">Bu derleyici seçeneği Visual Studio geliştirme ortamında kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-117">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="7d6b9-118">Bu derleyici seçeneği ile program aracılığıyla erişebilirsiniz <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-118">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d6b9-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d6b9-119">See Also</span></span>  
 [<span data-ttu-id="7d6b9-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="7d6b9-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="7d6b9-121">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="7d6b9-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
