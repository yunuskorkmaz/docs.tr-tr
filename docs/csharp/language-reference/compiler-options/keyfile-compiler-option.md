---
title: -keyfile (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: eef843c87b8f1993c3419b261894a6df31096294
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606894"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="84ebf-102">-keyfile (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="84ebf-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="84ebf-103">Şifreleme anahtarını içeren dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="84ebf-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84ebf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84ebf-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="84ebf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="84ebf-105">Arguments</span></span>  
  
|<span data-ttu-id="84ebf-106">Terim</span><span class="sxs-lookup"><span data-stu-id="84ebf-106">Term</span></span>|<span data-ttu-id="84ebf-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="84ebf-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="84ebf-108">Tanımlayıcı ad anahtarını içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="84ebf-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84ebf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84ebf-109">Remarks</span></span>  
 <span data-ttu-id="84ebf-110">Bu seçenek kullanıldığında, derleyici belirtilen dosyadan ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="84ebf-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="84ebf-111">Anahtar dosyası oluşturmak için komut satırına sn-k `file` yazın.</span><span class="sxs-lookup"><span data-stu-id="84ebf-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="84ebf-112">**-Target: Module**ile derleme yaparsanız, anahtar dosyasının adı modülde tutulur ve [-addmodule](./addmodule-compiler-option.md)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="84ebf-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="84ebf-113">Ayrıca, şifreleme bilgilerinizi [-keycontainer](./keycontainer-compiler-option.md)ile derleyiciye geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84ebf-113">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="84ebf-114">Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](./delaysign-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="84ebf-114">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="84ebf-115">Aynı derlemede hem-keyfile hem de-keycontainer belirtildiğinde (komut satırı seçeneği veya özel öznitelik tarafından), derleyici ilk olarak anahtar kapsayıcısını dener.</span><span class="sxs-lookup"><span data-stu-id="84ebf-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="84ebf-116">Bu başarılı olursa, derleme anahtar kapsayıcısındaki bilgilerle imzalanır.</span><span class="sxs-lookup"><span data-stu-id="84ebf-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="84ebf-117">Derleyici anahtar kapsayıcısını bulamazsa,-keyfile ile belirtilen dosyayı dener.</span><span class="sxs-lookup"><span data-stu-id="84ebf-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="84ebf-118">Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri, sonraki derlemede anahtar kapsayıcısının geçerli olacağı şekilde anahtar kapsayıcısına (sn-ı ' ye benzer) yüklenir.</span><span class="sxs-lookup"><span data-stu-id="84ebf-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="84ebf-119">Anahtar dosyasının yalnızca ortak anahtar içerebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="84ebf-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="84ebf-120">Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [bir derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="84ebf-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="84ebf-121">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="84ebf-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="84ebf-122">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="84ebf-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="84ebf-123">**İmzalama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="84ebf-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="84ebf-124">**Tanımlayıcı ad seçin anahtar dosyası** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="84ebf-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="84ebf-125">Bu derleyici seçeneğine <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>aracılığıyla programlı bir şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84ebf-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ebf-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84ebf-126">See also</span></span>

- [<span data-ttu-id="84ebf-127">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="84ebf-127">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="84ebf-128">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="84ebf-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
