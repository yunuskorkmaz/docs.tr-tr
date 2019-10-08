---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 15f334f280c2aca83ba5b628a1137464c31c6282
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005559"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="ee02a-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee02a-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="ee02a-103">Derleyicinin yalnızca belirtilen Visual Basic dil sürümünde bulunan sözdizimini kabul etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ee02a-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee02a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee02a-104">Syntax</span></span>  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee02a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ee02a-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="ee02a-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ee02a-106">Required.</span></span> <span data-ttu-id="ee02a-107">Derleme sırasında kullanılacak dil sürümü.</span><span class="sxs-lookup"><span data-stu-id="ee02a-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="ee02a-108">Kabul edilen değerler `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` ve `latest` ' dur.</span><span class="sxs-lookup"><span data-stu-id="ee02a-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` and `latest`.</span></span>

 <span data-ttu-id="ee02a-109">Tüm sayıların tamamı, ikincil sürüm olarak `.0` kullanılarak da belirtilebilir. Örneğin, `11.0`.</span><span class="sxs-lookup"><span data-stu-id="ee02a-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="ee02a-110">Komut satırında `-langversion:?` belirterek, olası tüm değerlerin listesini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee02a-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee02a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee02a-111">Remarks</span></span>  
 <span data-ttu-id="ee02a-112">@No__t-0 seçeneği derleyicinin kabul ettiği sözdizimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee02a-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="ee02a-113">Örneğin, dil sürümünün 9,0 olduğunu belirtirseniz, derleyici yalnızca 10,0 ve sonraki sürümlerde geçerli olan sözdizimi için hatalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ee02a-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="ee02a-114">.NET Framework farklı sürümlerini hedefleyen uygulamalar geliştirirken, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee02a-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="ee02a-115">Örneğin, .NET Framework 3,5 ' i hedefliyorsanız, dil sürümü 10,0 ' den sözdizimini kullanmamanız için bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee02a-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="ee02a-116">Yalnızca komut satırını kullanarak doğrudan `-langversion` ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee02a-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="ee02a-117">Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="ee02a-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee02a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee02a-118">Example</span></span>  
 <span data-ttu-id="ee02a-119">Aşağıdaki kod, Visual Basic 9,0 için `sample.vb` derler.</span><span class="sxs-lookup"><span data-stu-id="ee02a-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee02a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee02a-120">See also</span></span>

- [<span data-ttu-id="ee02a-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ee02a-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ee02a-122">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ee02a-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="ee02a-123">Belirli Bir .NET Framework Sürümünü Hedefleme</span><span class="sxs-lookup"><span data-stu-id="ee02a-123">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
