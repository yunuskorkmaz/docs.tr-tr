---
title: /langversion (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cfe91588471cc8410b25addea8d66a0388c9c5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-visual-basic"></a><span data-ttu-id="d543e-102">/langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d543e-102">/langversion (Visual Basic)</span></span>
<span data-ttu-id="d543e-103">Derleyicinin yalnızca belirtilen Visual Basic dil sürümü dahil sözdizimini kabul etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d543e-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d543e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d543e-104">Syntax</span></span>  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="d543e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d543e-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="d543e-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d543e-106">Required.</span></span> <span data-ttu-id="d543e-107">Derleme sırasında kullanılacak dil sürümü.</span><span class="sxs-lookup"><span data-stu-id="d543e-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="d543e-108">Değerler kabul `9`, `9.0`, `10`, ve `10.0`.</span><span class="sxs-lookup"><span data-stu-id="d543e-108">Accepted values are `9`, `9.0`, `10`, and `10.0`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d543e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d543e-109">Remarks</span></span>  
 <span data-ttu-id="d543e-110">`/langversion` Seçeneği derleyici kabul hangi sözdizimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d543e-110">The `/langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="d543e-111">Örneğin, dil sürümü 9.0 olduğunu belirtirseniz, derleyici geçerli yalnızca sürümünde 10.0 ve sonraki sözdizimi hataları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d543e-111">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="d543e-112">Bu hedef farklı sürümlerini .NET Framework uygulamaları geliştirirken, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d543e-112">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="d543e-113">Örneğin, .NET Framework 3.5 hedefliyorsanız, 10.0 dil sürümünden sözdizimi kullanmayın emin olmak için bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d543e-113">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="d543e-114">Ayarlayabileceğiniz `/langversion` doğrudan komut satırını kullanarak yalnızca.</span><span class="sxs-lookup"><span data-stu-id="d543e-114">You can set `/langversion` directly only by using the command line.</span></span> <span data-ttu-id="d543e-115">Daha fazla bilgi için bkz: [belirli bir .NET Framework sürümü hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="d543e-115">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d543e-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="d543e-116">Example</span></span>  
 <span data-ttu-id="d543e-117">Aşağıdaki kod derlerken `sample.vb` Visual Basic 9.0.</span><span class="sxs-lookup"><span data-stu-id="d543e-117">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d543e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d543e-118">See Also</span></span>  
 [<span data-ttu-id="d543e-119">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d543e-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d543e-120">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="d543e-120">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d543e-121">Belirli bir .NET Framework sürümünü hedefleme</span><span class="sxs-lookup"><span data-stu-id="d543e-121">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
