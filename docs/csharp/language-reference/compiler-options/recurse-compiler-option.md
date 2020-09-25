---
description: -recurse (C# derleyici seçenekleri)
title: -recurse (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 9e84ff95f7f0addac1c2c2d79af0ab53572da27f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193809"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="395ac-103">-recurse (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="395ac-103">-recurse (C# Compiler Options)</span></span>

<span data-ttu-id="395ac-104">-Recurse seçeneği, belirtilen dizinin (dir) veya proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="395ac-104">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="395ac-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="395ac-105">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="395ac-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="395ac-106">Arguments</span></span>  

 <span data-ttu-id="395ac-107">`dir` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="395ac-107">`dir` (optional)</span></span>  
 <span data-ttu-id="395ac-108">Aramanın başlamasını istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="395ac-108">The directory in which you want the search to begin.</span></span> <span data-ttu-id="395ac-109">Bu belirtilmemişse, arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="395ac-109">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="395ac-110">Aranacak dosya (lar).</span><span class="sxs-lookup"><span data-stu-id="395ac-110">The file(s) to search for.</span></span> <span data-ttu-id="395ac-111">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="395ac-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="395ac-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="395ac-112">Remarks</span></span>  

 <span data-ttu-id="395ac-113">**-Recurse** seçeneği, kaynak kodu dosyalarını belirtilen dizinin ( `dir` ) veya proje dizininin tüm alt dizinlerinde derlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="395ac-113">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="395ac-114">Proje dizinindeki tüm eşleşen dosyaları **-Recurse**kullanmadan derlemek için dosya adında joker karakterler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="395ac-114">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="395ac-115">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="395ac-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="395ac-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="395ac-116">Example</span></span>  

 <span data-ttu-id="395ac-117">Geçerli dizindeki tüm C# dosyalarını derler:</span><span class="sxs-lookup"><span data-stu-id="395ac-117">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="395ac-118">Dir1\dir2 dizinindeki tüm C# dosyalarını ve altındaki tüm dizinleri derler ve dir2.dll üretir:</span><span class="sxs-lookup"><span data-stu-id="395ac-118">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="395ac-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="395ac-119">See also</span></span>

- [<span data-ttu-id="395ac-120">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="395ac-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="395ac-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="395ac-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
