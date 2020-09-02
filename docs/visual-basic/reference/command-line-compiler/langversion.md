---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.custom: updateeachrelease
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 9921df0b8bb1a4808528b58a5a38d75e5e3fbdd2
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359265"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="182d1-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="182d1-102">-langversion (Visual Basic)</span></span>

<span data-ttu-id="182d1-103">Derleyicinin yalnızca belirtilen Visual Basic dil sürümünde bulunan sözdizimini kabul etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="182d1-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182d1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="182d1-104">Syntax</span></span>  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="182d1-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="182d1-105">Arguments</span></span>

 `version`\
 <span data-ttu-id="182d1-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="182d1-106">Required.</span></span> <span data-ttu-id="182d1-107">Derleme sırasında kullanılacak dil sürümü.</span><span class="sxs-lookup"><span data-stu-id="182d1-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="182d1-108">Kabul edilen değerler şunlardır,,,,,, `9` `10` `11` `12` `14` `15` `15.3` , `15.5` , `16` `default` ve `latest` .</span><span class="sxs-lookup"><span data-stu-id="182d1-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `16`, `default` and `latest`.</span></span>

 <span data-ttu-id="182d1-109">Tüm sayıların tümü, alt sürüm olarak (örneğin,) kullanılarak da belirtilebilir `.0` `11.0` .</span><span class="sxs-lookup"><span data-stu-id="182d1-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="182d1-110">Komut satırında belirterek, olası tüm değerlerin listesini görebilirsiniz `-langversion:?` .</span><span class="sxs-lookup"><span data-stu-id="182d1-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="182d1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="182d1-111">Remarks</span></span>

<span data-ttu-id="182d1-112">`-langversion`Seçeneği derleyicinin kabul ettiği sözdizimini belirtir.</span><span class="sxs-lookup"><span data-stu-id="182d1-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="182d1-113">Örneğin, dil sürümünün 9,0 olduğunu belirtirseniz, derleyici yalnızca 10,0 ve sonraki sürümlerde geçerli olan sözdizimi için hatalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="182d1-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>

<span data-ttu-id="182d1-114">.NET Framework farklı sürümlerini hedefleyen uygulamalar geliştirirken, bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="182d1-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="182d1-115">Örneğin, .NET Framework 3,5 ' i hedefliyorsanız, dil sürümü 10,0 ' den sözdizimini kullanmamanız için bu seçeneği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="182d1-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>

<span data-ttu-id="182d1-116">`-langversion`Doğrudan yalnızca komut satırını kullanarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="182d1-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="182d1-117">Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](/visualstudio/ide/visual-studio-multi-targeting-overview).</span><span class="sxs-lookup"><span data-stu-id="182d1-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/visual-studio-multi-targeting-overview).</span></span>

## <a name="example"></a><span data-ttu-id="182d1-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="182d1-118">Example</span></span>

<span data-ttu-id="182d1-119">Aşağıdaki kod `sample.vb` Visual Basic 9,0 için derlenir.</span><span class="sxs-lookup"><span data-stu-id="182d1-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>

```console
vbc -langversion:9.0 sample.vb
```

## <a name="see-also"></a><span data-ttu-id="182d1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="182d1-120">See also</span></span>

- [<span data-ttu-id="182d1-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="182d1-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="182d1-122">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="182d1-122">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
