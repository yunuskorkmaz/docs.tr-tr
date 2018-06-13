---
title: -recurse (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 7d18fb2b1710e074653e054d003be762d947d1be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214595"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="34799-102">-recurse (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="34799-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="34799-103">Recurse seçeneği, belirtilen dizin (dir) veya proje dizininin tüm alt dizinlerdeki kaynak kodu dosyaları derlemek sağlar.</span><span class="sxs-lookup"><span data-stu-id="34799-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34799-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34799-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="34799-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="34799-105">Arguments</span></span>  
 <span data-ttu-id="34799-106">`dir` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="34799-106">`dir` (optional)</span></span>  
 <span data-ttu-id="34799-107">Aramayı başlatmak istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="34799-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="34799-108">Bu belirtilmezse arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="34799-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="34799-109">Aranacak dosya.</span><span class="sxs-lookup"><span data-stu-id="34799-109">The file(s) to search for.</span></span> <span data-ttu-id="34799-110">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="34799-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34799-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34799-111">Remarks</span></span>  
 <span data-ttu-id="34799-112">**-Recurse** seçeneği belirtilen dizinin tüm alt dizinlerdeki kaynak kodu dosyaları derleme olanak tanır (`dir`) veya proje dizininin.</span><span class="sxs-lookup"><span data-stu-id="34799-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="34799-113">Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için dosya adında joker karakterleri kullanabilirsiniz **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="34799-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="34799-114">Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="34799-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34799-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="34799-115">Example</span></span>  
 <span data-ttu-id="34799-116">Geçerli dizindeki tüm C# dosyalarını derler:</span><span class="sxs-lookup"><span data-stu-id="34799-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="34799-117">C# dosyalarını dir1\dir2 dizininde tümüne ve altındaki herhangi bir dizin derler ve dir2.dll oluşturur:</span><span class="sxs-lookup"><span data-stu-id="34799-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="34799-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34799-118">See Also</span></span>  
 [<span data-ttu-id="34799-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="34799-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="34799-120">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="34799-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
