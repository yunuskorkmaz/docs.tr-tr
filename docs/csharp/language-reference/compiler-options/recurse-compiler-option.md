---
title: -recurse (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606746"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="0c814-102">-recurse (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="0c814-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="0c814-103">-Recurse seçeneği, belirtilen dizinin (dir) veya proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c814-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c814-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c814-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c814-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0c814-105">Arguments</span></span>  
 <span data-ttu-id="0c814-106">`dir`seçim</span><span class="sxs-lookup"><span data-stu-id="0c814-106">`dir` (optional)</span></span>  
 <span data-ttu-id="0c814-107">Aramanın başlamasını istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="0c814-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="0c814-108">Bu belirtilmemişse, arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="0c814-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="0c814-109">Aranacak dosya (lar).</span><span class="sxs-lookup"><span data-stu-id="0c814-109">The file(s) to search for.</span></span> <span data-ttu-id="0c814-110">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="0c814-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c814-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c814-111">Remarks</span></span>  
 <span data-ttu-id="0c814-112">**-Recurse** seçeneği, kaynak kodu dosyalarını belirtilen dizinin (`dir`) veya proje dizininin tüm alt dizinlerinde derlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0c814-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="0c814-113">Proje dizinindeki tüm eşleşen dosyaları **-Recurse**kullanmadan derlemek için dosya adında joker karakterler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c814-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="0c814-114">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="0c814-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c814-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c814-115">Example</span></span>  
 <span data-ttu-id="0c814-116">Geçerli dizindeki C# tüm dosyaları derler:</span><span class="sxs-lookup"><span data-stu-id="0c814-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="0c814-117">Dir1\dir2 dizinindeki tüm C# dosyaları ve bunun altındaki dizinleri derler ve dir2. dll oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0c814-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c814-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c814-118">See also</span></span>

- [<span data-ttu-id="0c814-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0c814-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="0c814-120">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="0c814-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
