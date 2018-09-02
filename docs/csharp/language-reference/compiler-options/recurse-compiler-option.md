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
ms.openlocfilehash: 1fc5591cb73164e15384eb4407a6e61e903eedbb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398783"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="62f10-102">-recurse (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="62f10-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="62f10-103">Recurse seçenek, tüm alt dizinleri belirtilen dizin (dizini) veya proje dizininin kaynak kodu dosyalarını derlemek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="62f10-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62f10-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="62f10-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="62f10-105">Arguments</span></span>  
 <span data-ttu-id="62f10-106">`dir` (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="62f10-106">`dir` (optional)</span></span>  
 <span data-ttu-id="62f10-107">Aramayı başlatmak istediğiniz dizin.</span><span class="sxs-lookup"><span data-stu-id="62f10-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="62f10-108">Bu seçenek belirtilmezse arama proje dizininde başlar.</span><span class="sxs-lookup"><span data-stu-id="62f10-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="62f10-109">Aranacak dosya.</span><span class="sxs-lookup"><span data-stu-id="62f10-109">The file(s) to search for.</span></span> <span data-ttu-id="62f10-110">Joker karakterlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="62f10-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62f10-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62f10-111">Remarks</span></span>  
 <span data-ttu-id="62f10-112">**-Recurse** belirtilen dizinin tüm alt dizinlerdeki kaynak kodu dosyaları derleme seçeneği sağlar (`dir`) veya proje dizini.</span><span class="sxs-lookup"><span data-stu-id="62f10-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="62f10-113">Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için bir dosya adında joker karakterler kullanabilirsiniz **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="62f10-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="62f10-114">Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="62f10-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62f10-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="62f10-115">Example</span></span>  
 <span data-ttu-id="62f10-116">Geçerli dizindeki tüm C# dosyaları derler:</span><span class="sxs-lookup"><span data-stu-id="62f10-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="62f10-117">Tüm dir1\dir2 dizinde C# dosyaları ve dizinleri aşağıdaki derler ve dir2.dll oluşturur:</span><span class="sxs-lookup"><span data-stu-id="62f10-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="62f10-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62f10-118">See Also</span></span>  

- [<span data-ttu-id="62f10-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="62f10-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="62f10-120">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="62f10-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
