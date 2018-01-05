---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4d29f99d0c375eebee0f477720cb9a22172dddb
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="delaysign"></a><span data-ttu-id="9e8bd-102">/delaysign</span><span class="sxs-lookup"><span data-stu-id="9e8bd-102">/delaysign</span></span>
<span data-ttu-id="9e8bd-103">Derlemenin tamamen veya kısmen imzalanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e8bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e8bd-104">Syntax</span></span>  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e8bd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9e8bd-105">Arguments</span></span>  
 <span data-ttu-id="9e8bd-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="9e8bd-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="9e8bd-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-107">Optional.</span></span> <span data-ttu-id="9e8bd-108">Kullanım `/delaysign-` tam imzalı bir derleme istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-108">Use `/delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="9e8bd-109">Kullanım `/delaysign+` imzalı karma için derleme ve ayrılmış alanı ortak anahtarı koyun istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-109">Use `/delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="9e8bd-110">Varsayılan, `/delaysign-` değeridir.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-110">The default is `/delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e8bd-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e8bd-111">Remarks</span></span>  
 <span data-ttu-id="9e8bd-112">`/delaysign` Seçeneği hiçbir etkisi ile kullanılmadığı sürece [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) veya [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="9e8bd-112">The `/delaysign` option has no effect unless used with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="9e8bd-113">Tam imzalı bir derleme istediğinde bildirimi (derleme meta verilerini) içeren ve karmayı özel anahtarıyla imzalar dosyayı derleyici karma hale getirir.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="9e8bd-114">Elde edilen dijital imza, bildirimi içeren dosyada depolanır.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="9e8bd-115">Bir derlemeyi imzalı gecikme olduğunda derleyici işlem değil ve daha sonra imzanın eklenmesi için imza ancak yedekleri alanı dosyasında depolamak.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="9e8bd-116">Kullanarak örneğin, `/delaysign+`, bir kuruluştaki bir geliştirici sınayıcılar genel derleme önbelleği ile kaydetmek ve kullanabilecek bir derlemeyi imzasız test sürümlerini dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-116">For example, by using `/delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="9e8bd-117">Derleme üzerinde iş tamamlandığında, kuruluşunuzun özel anahtarı sorumlu kişi derleme tam olarak oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="9e8bd-118">Bu compartmentalization tüm geliştiricilerin derlemelerini sağlarken kuruluşunuzun özel anahtarı ifşaatına karşı korur.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="9e8bd-119">Bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) derleme imzalama hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-119">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="9e8bd-120">Tümleşik geliştirme ortamı/delaysign Visual Studio'da ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9e8bd-120">To set /delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="9e8bd-121">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9e8bd-122">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-122">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="9e8bd-123">Tıklatın **imzalama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-123">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="9e8bd-124">Değer kümesinde **gecikme yalnızca oturum** kutusu.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e8bd-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e8bd-125">See Also</span></span>  
 [<span data-ttu-id="9e8bd-126">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="9e8bd-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9e8bd-127">/keyfile</span><span class="sxs-lookup"><span data-stu-id="9e8bd-127">/keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="9e8bd-128">/keycontainer</span><span class="sxs-lookup"><span data-stu-id="9e8bd-128">/keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="9e8bd-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="9e8bd-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
