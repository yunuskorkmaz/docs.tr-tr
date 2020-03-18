---
title: -keyfile (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970254"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="a28e2-102">-keyfile (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a28e2-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="a28e2-103">Şifreleme anahtarını içeren dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a28e2-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a28e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a28e2-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="a28e2-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="a28e2-105">Arguments</span></span>  
  
|<span data-ttu-id="a28e2-106">Sözleşme Dönemi</span><span class="sxs-lookup"><span data-stu-id="a28e2-106">Term</span></span>|<span data-ttu-id="a28e2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="a28e2-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="a28e2-108">Güçlü ad anahtarını içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a28e2-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a28e2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a28e2-109">Remarks</span></span>  
 <span data-ttu-id="a28e2-110">Bu seçenek kullanıldığında, derleyici belirtilen dosyadan ortak anahtarı derleme bildirimine ekler ve sonra son derlemeyi özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="a28e2-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="a28e2-111">Anahtar dosyası oluşturmak için komut satırına sn -k `file` yazın.</span><span class="sxs-lookup"><span data-stu-id="a28e2-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="a28e2-112">**-target:module**ile derlerseniz, anahtar dosyasının adı modülde tutulur ve [-addmodule](./addmodule-compiler-option.md)ile bir derleme derlediğinizde oluşturulan derlemeye dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="a28e2-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="a28e2-113">Şifreleme bilgilerinizi [-keycontainer](./keycontainer-compiler-option.md)ile derleyiciye de iletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a28e2-113">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="a28e2-114">Kısmen imzalanmış bir montaj istiyorsanız [-delaysign](./delaysign-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a28e2-114">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="a28e2-115">Aynı derlemede hem -keyfile hem de -keycontainer (komut satırı seçeneği yle veya özel öznitelik ile) belirtilirse, derleyici önce anahtar kapsayıcısını dener.</span><span class="sxs-lookup"><span data-stu-id="a28e2-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="a28e2-116">Bu başarılı olursa, o zaman derleme anahtar kapsayıcısında bilgi ile imzalanır.</span><span class="sxs-lookup"><span data-stu-id="a28e2-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="a28e2-117">Derleyici anahtar kapsayıcısını bulamazsa, -keyfile ile belirtilen dosyayı dener.</span><span class="sxs-lookup"><span data-stu-id="a28e2-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="a28e2-118">Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısına (sn-i'ye benzer) yüklenir, böylece bir sonraki derlemede anahtar kapsayıcı geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="a28e2-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="a28e2-119">Anahtar dosyasının yalnızca ortak anahtarı içerebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a28e2-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="a28e2-120">Daha fazla bilgi için [bkz.](../../../standard/assembly/create-use-strong-named.md) [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md)</span><span class="sxs-lookup"><span data-stu-id="a28e2-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a28e2-121">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a28e2-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a28e2-122">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="a28e2-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="a28e2-123">**İmzalama** özelliği sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a28e2-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="a28e2-124">Güçlü **bir ad anahtarı dosya özelliğini seçin.**</span><span class="sxs-lookup"><span data-stu-id="a28e2-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="a28e2-125">Bu derleyici seçeneğine programlı <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>olarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a28e2-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a28e2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a28e2-126">See also</span></span>

- [<span data-ttu-id="a28e2-127">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a28e2-127">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a28e2-128">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="a28e2-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
