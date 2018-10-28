---
title: -delaysıgn
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 1459484b858137836fcfdcd9db46d8e99a06e9c7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185215"
---
# <a name="-delaysign"></a><span data-ttu-id="ff6c1-102">-delaysıgn</span><span class="sxs-lookup"><span data-stu-id="ff6c1-102">-delaysign</span></span>
<span data-ttu-id="ff6c1-103">Derlemenin tamamen veya kısmen imzalanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff6c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff6c1-104">Syntax</span></span>  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff6c1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ff6c1-105">Arguments</span></span>  
 <span data-ttu-id="ff6c1-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ff6c1-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="ff6c1-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-107">Optional.</span></span> <span data-ttu-id="ff6c1-108">Kullanım `-delaysign-` tam imzalı bir derleme istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="ff6c1-109">Kullanım `-delaysign+` , derleme ve ayrılan alana imzalı karma için ortak anahtar yerleştirmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="ff6c1-110">Varsayılan, `-delaysign-` değeridir.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff6c1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff6c1-111">Remarks</span></span>  
 <span data-ttu-id="ff6c1-112">`-delaysign` Seçeneği ile birlikte kullanılmadığı sürece hiçbir etkiye sahiptir [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) veya [- keycontaıner](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="ff6c1-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="ff6c1-113">Tam imzalı bir derleme istediğinizde; derleyici bildirimi (derleme meta verileri) içeren ve karmayı özel anahtarla imzalar dosyayı karma hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="ff6c1-114">Elde edilen dijital imza, bildirimi içeren dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="ff6c1-115">Bir derlemeyi gecikmeli imzalanmış olduğunda, derleyici işlem değildir ve daha sonra imzanın eklenmesi için dosyada imza ancak yedekleri alanı depolamak.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="ff6c1-116">Kullanarak örneğin, `-delaysign+`, bir kuruluşta bir geliştirici, test ediciler genel derleme önbelleği ile kaydedebilir veya kullanmak bir derleme sürümlerini imzasız test dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="ff6c1-117">Derleme üzerinde iş tamamlandığında, kuruluşun özel anahtarı için sorumlu kişi derleme tam olarak imzalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="ff6c1-118">Bu compartmentalization, kuruluşunuzun özel anahtarı derlemelerini çalışması tüm geliştiricilerin verirken ifşaatına karşı korur.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="ff6c1-119">Bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) derleme imzalama hakkında daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-119">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="ff6c1-120">-Delaysıgn Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ff6c1-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="ff6c1-121">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ff6c1-122">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-122">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="ff6c1-123">Tıklayın **imzalama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-123">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="ff6c1-124">Değer kümesindeki **gecikme yalnızca oturum** kutusu.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6c1-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff6c1-125">See Also</span></span>  
 [<span data-ttu-id="ff6c1-126">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ff6c1-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ff6c1-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="ff6c1-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="ff6c1-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="ff6c1-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="ff6c1-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ff6c1-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
