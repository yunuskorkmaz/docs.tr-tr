---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 6fffe264377474bba14f6f086b521ccf9bd04adf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534465"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="94d9e-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94d9e-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="94d9e-103">Derleyicinin, belirtilen Visual Basic dil sürümü dahil edilen sözdizimini kabul etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="94d9e-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94d9e-104">Syntax</span></span>  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="94d9e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="94d9e-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="94d9e-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="94d9e-106">Required.</span></span> <span data-ttu-id="94d9e-107">Derleme sırasında kullanılacak dil sürümü.</span><span class="sxs-lookup"><span data-stu-id="94d9e-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="94d9e-108">Kabul edilen değerler `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` ve `latest`.</span><span class="sxs-lookup"><span data-stu-id="94d9e-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` and `latest`.</span></span>

 <span data-ttu-id="94d9e-109">Tam sayılar da kullanırken belirtilebilir `.0` alt sürümü için olarak `11.0`.</span><span class="sxs-lookup"><span data-stu-id="94d9e-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="94d9e-110">Tüm olası değerlerin listesi belirterek gördüğünüz `-langversion:?` komut satırında.</span><span class="sxs-lookup"><span data-stu-id="94d9e-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94d9e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94d9e-111">Remarks</span></span>  
 <span data-ttu-id="94d9e-112">`-langversion` Seçeneği derleyici kabul hangi sözdizimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="94d9e-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="94d9e-113">Örneğin, dil sürüm 9.0 olduğunu belirtirseniz, derleyici geçerli yalnızca sürüm 10.0 ve üstü söz dizimi hataları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94d9e-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="94d9e-114">Farklı sürümlerini hedefleyen .NET Framework'ün Uygulama geliştirirken, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94d9e-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="94d9e-115">Örneğin, .NET Framework 3.5 hedefliyorsanız, dil sürüm 10.0 sözdizimini kullanmayın emin olmak için bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94d9e-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="94d9e-116">Ayarlayabileceğiniz `-langversion` doğrudan komut satırını kullanarak yalnızca.</span><span class="sxs-lookup"><span data-stu-id="94d9e-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="94d9e-117">Daha fazla bilgi için [belirli bir .NET Framework sürümünü hedefleme](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="94d9e-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94d9e-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="94d9e-118">Example</span></span>  
 <span data-ttu-id="94d9e-119">Aşağıdaki kod derlenir `sample.vb` Visual Basic 9.0.</span><span class="sxs-lookup"><span data-stu-id="94d9e-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="94d9e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94d9e-120">See also</span></span>
- [<span data-ttu-id="94d9e-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="94d9e-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="94d9e-122">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="94d9e-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="94d9e-123">Belirli Bir .NET Framework Sürümünü Hedefleme</span><span class="sxs-lookup"><span data-stu-id="94d9e-123">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
