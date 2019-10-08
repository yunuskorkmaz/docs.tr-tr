---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 66edc45c622b78187469ccc0631beb53b68049b0
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002303"
---
# <a name="-delaysign"></a><span data-ttu-id="5f899-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="5f899-102">-delaysign</span></span>
<span data-ttu-id="5f899-103">Derlemenin tamamen veya kısmen imzalanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f899-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f899-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f899-104">Syntax</span></span>  
  
```console  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5f899-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5f899-105">Arguments</span></span>  
 <span data-ttu-id="5f899-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5f899-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="5f899-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5f899-107">Optional.</span></span> <span data-ttu-id="5f899-108">Tam olarak imzalanan bir derleme istiyorsanız `-delaysign-` kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f899-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="5f899-109">Ortak anahtarı derlemeye koymak ve imzalı karma için alan ayırmak istiyorsanız `-delaysign+` kullanın.</span><span class="sxs-lookup"><span data-stu-id="5f899-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="5f899-110">Varsayılan, `-delaysign-` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5f899-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f899-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f899-111">Remarks</span></span>  
 <span data-ttu-id="5f899-112">[-Keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) veya [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)ile kullanılmamışsa `-delaysign` seçeneğinin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5f899-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="5f899-113">Tam olarak imzalanan bir derleme istediğinizde, derleyici bildirimi içeren dosyayı (derleme meta verileri) karma hale getirir ve bu karmayı özel anahtarla imzalar.</span><span class="sxs-lookup"><span data-stu-id="5f899-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="5f899-114">Elde edilen dijital imza, bildirimi içeren dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="5f899-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="5f899-115">Bir derlemenin gecikmesi gecikmeli olduğunda, derleyici imzayı hesaplamaz ve depolamaz, ancak imza daha sonra eklenebilmesi için dosyada yer ayırır.</span><span class="sxs-lookup"><span data-stu-id="5f899-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="5f899-116">Örneğin, `-delaysign+` ' ı kullanarak bir kuruluştaki geliştirici, test edicinin genel derleme önbelleği ile kaydedebilmesi ve kullanması için imzasız test sürümlerini dağıtabilir.</span><span class="sxs-lookup"><span data-stu-id="5f899-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="5f899-117">Derlemedeki iş tamamlandığında, kuruluşun özel anahtarından sorumlu olan kişi derlemeyi tamamen imzalayabilir.</span><span class="sxs-lookup"><span data-stu-id="5f899-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="5f899-118">Bu compartmen, kuruluşun özel anahtarının açıklanmasını koruurken tüm geliştiricilerin derlemeler üzerinde çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5f899-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="5f899-119">Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı adlı derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="5f899-119">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="5f899-120">Visual Studio tümleşik geliştirme ortamında Set-delaysign</span><span class="sxs-lookup"><span data-stu-id="5f899-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="5f899-121">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f899-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5f899-122">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5f899-122">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="5f899-123">**İmzalama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5f899-123">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="5f899-124">Değeri **yalnızca gecikmeli imzala** kutusunda ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5f899-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f899-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f899-125">See also</span></span>

- [<span data-ttu-id="5f899-126">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="5f899-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="5f899-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="5f899-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="5f899-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="5f899-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [<span data-ttu-id="5f899-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="5f899-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
