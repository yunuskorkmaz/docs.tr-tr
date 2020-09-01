---
description: -pathmap (C# derleyici seçenekleri)
title: -pathmap (C# derleyici seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 707a37c6946cfcaf429552f0aeece6b87f3ad71d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125013"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="15ba4-103">-pathmap (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="15ba4-103">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="15ba4-104">**-Pathmap** derleyici seçeneği, fiziksel yolların derleyicinin çıkış kaynak yol adlarına nasıl eşlendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="15ba4-104">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="15ba4-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="15ba4-105">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="15ba4-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="15ba4-106">Arguments</span></span>

 <span data-ttu-id="15ba4-107">`path1` Geçerli ortamdaki kaynak dosyalarının tam yolu</span><span class="sxs-lookup"><span data-stu-id="15ba4-107">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="15ba4-108">`sourcePath1` Her çıkış dosyasında yerine geçen kaynak yol `path1` .</span><span class="sxs-lookup"><span data-stu-id="15ba4-108">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="15ba4-109">Birden çok eşlenmiş kaynak yolunu belirtmek için, her biri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="15ba4-109">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="15ba4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15ba4-110">Remarks</span></span>

<span data-ttu-id="15ba4-111">Derleyici, kaynak yolunu aşağıdaki nedenlerden dolayı çıktısına yazar:</span><span class="sxs-lookup"><span data-stu-id="15ba4-111">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="15ba4-112">İsteğe bağlı bir parametreye uygulandığında kaynak yolu bir bağımsız değişken için değiştirilir <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> .</span><span class="sxs-lookup"><span data-stu-id="15ba4-112">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="15ba4-113">Kaynak yolu bir PDB dosyasına katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="15ba4-113">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="15ba4-114">PDB dosyasının yolu bir PE (taşınabilir yürütülebilir) dosyasına katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="15ba4-114">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="15ba4-115">Bu seçenek, derleyicinin çalıştığı makinedeki her fiziksel yolu, çıktı dosyalarında yazılması gereken karşılık gelen bir yola eşler.</span><span class="sxs-lookup"><span data-stu-id="15ba4-115">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="15ba4-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="15ba4-116">Example</span></span>

<span data-ttu-id="15ba4-117">`t.cs` **C: \\ iş \\ testlerinde** derleyin ve bu dizini çıktıda **\publish** ile eşleyin:</span><span class="sxs-lookup"><span data-stu-id="15ba4-117">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="15ba4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15ba4-118">See also</span></span>

- [<span data-ttu-id="15ba4-119">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="15ba4-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="15ba4-120">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="15ba4-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
