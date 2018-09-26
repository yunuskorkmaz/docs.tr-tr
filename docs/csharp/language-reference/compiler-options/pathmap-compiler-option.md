---
title: -pathmap (C# Derleyici Seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 277ab8e094f28fd5e3cbba4de12e742bb9614730
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077025"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="65754-102">-pathmap (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="65754-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="65754-103">**- Pathmap** derleyici seçeneği, fiziksel yollar, derleyici tarafından kaynak yol adları çıktısına eşlemeyle ilgili bilgi belirtir.</span><span class="sxs-lookup"><span data-stu-id="65754-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="65754-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65754-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="65754-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="65754-105">Arguments</span></span>

 <span data-ttu-id="65754-106">`path1` Geçerli ortamda kaynak dosyalarının tam yolu</span><span class="sxs-lookup"><span data-stu-id="65754-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="65754-107">`sourcePath1` Kaynak yolu için yerine `path1` herhangi bir çıktı dosyaları içinde.</span><span class="sxs-lookup"><span data-stu-id="65754-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="65754-108">Birden çok eşleşen kaynak yolları belirlemek için her virgül ile ayırın.</span><span class="sxs-lookup"><span data-stu-id="65754-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="65754-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65754-109">Remarks</span></span>

<span data-ttu-id="65754-110">Derleyici, aşağıdaki nedenlerden dolayı çıktısını kaynak yol Yazar:</span><span class="sxs-lookup"><span data-stu-id="65754-110">The compiler writes the source path path into its output for the following reasons:</span></span>

1. <span data-ttu-id="65754-111">Kaynak yolu için bağımsız değişken yerine zaman <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> için isteğe bağlı parametresi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="65754-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="65754-112">Kaynak yolu bir PDB dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="65754-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="65754-113">PDB dosyasının yolu (taşınabilir çalıştırılabilir) PE dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="65754-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="65754-114">Bu seçenek derleyici çıktı dosyaları yazılmalıdır karşılık gelen bir yola çalıştırıldığı makine üzerinde her fiziksel yolu eşler.</span><span class="sxs-lookup"><span data-stu-id="65754-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="65754-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="65754-115">Example</span></span>

<span data-ttu-id="65754-116">Derleme `t.cs` dizinde **C:\\çalışma\\testleri** ve bu dizine harita **\publish** çıktı:</span><span class="sxs-lookup"><span data-stu-id="65754-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="65754-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65754-117">See also</span></span>

- [<span data-ttu-id="65754-118">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="65754-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="65754-119">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="65754-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
