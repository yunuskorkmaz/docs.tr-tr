---
description: :-Langversion (Visual Basic) hakkında daha fazla bilgi edinin
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.custom: updateeachrelease
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 52bf910e5d6f579ec535d9de5698a8921f058002
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466867"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="b2611-103">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2611-103">-langversion (Visual Basic)</span></span>

<span data-ttu-id="b2611-104">Derleyicinin yalnızca belirtilen Visual Basic dil sürümünde bulunan sözdizimini kabul etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="b2611-104">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2611-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b2611-105">Syntax</span></span>  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="b2611-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b2611-106">Arguments</span></span>

 `version`\
 <span data-ttu-id="b2611-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b2611-107">Required.</span></span> <span data-ttu-id="b2611-108">Derleme sırasında kullanılacak dil sürümü.</span><span class="sxs-lookup"><span data-stu-id="b2611-108">The language version to be used during the compilation.</span></span> <span data-ttu-id="b2611-109">Kabul edilen değerler şunlardır,,,,,, `9` `10` `11` `12` `14` `15` `15.3` , `15.5` , `16` `default` ve `latest` .</span><span class="sxs-lookup"><span data-stu-id="b2611-109">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `16`, `default` and `latest`.</span></span>

 <span data-ttu-id="b2611-110">Tüm sayıların tümü, alt sürüm olarak (örneğin,) kullanılarak da belirtilebilir `.0` `11.0` .</span><span class="sxs-lookup"><span data-stu-id="b2611-110">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="b2611-111">Komut satırında belirterek, olası tüm değerlerin listesini görebilirsiniz `-langversion:?` .</span><span class="sxs-lookup"><span data-stu-id="b2611-111">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2611-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2611-112">Remarks</span></span>

<span data-ttu-id="b2611-113">`-langversion`Seçeneği derleyicinin kabul ettiği sözdizimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2611-113">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="b2611-114">Örneğin, dil sürümünün 9,0 olduğunu belirtirseniz, derleyici yalnızca 10,0 ve sonraki sürümlerde geçerli olan sözdizimi için hatalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2611-114">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>

<span data-ttu-id="b2611-115">.NET Framework farklı sürümlerini hedefleyen uygulamalar geliştirirken, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2611-115">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="b2611-116">Örneğin, .NET Framework 3,5 ' i hedefliyorsanız, dil sürümü 10,0 ' den sözdizimini kullanmamanız için bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2611-116">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>

<span data-ttu-id="b2611-117">`-langversion`Doğrudan yalnızca komut satırını kullanarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2611-117">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="b2611-118">Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](/visualstudio/ide/visual-studio-multi-targeting-overview).</span><span class="sxs-lookup"><span data-stu-id="b2611-118">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/visual-studio-multi-targeting-overview).</span></span>

## <a name="example"></a><span data-ttu-id="b2611-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2611-119">Example</span></span>

<span data-ttu-id="b2611-120">Aşağıdaki kod `sample.vb` Visual Basic 9,0 için derlenir.</span><span class="sxs-lookup"><span data-stu-id="b2611-120">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>

```console
vbc -langversion:9.0 sample.vb
```

## <a name="see-also"></a><span data-ttu-id="b2611-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2611-121">See also</span></span>

- [<span data-ttu-id="b2611-122">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b2611-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b2611-123">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b2611-123">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
