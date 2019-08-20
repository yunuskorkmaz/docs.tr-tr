---
title: -pathmap (C# derleyici seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606634"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="dda10-102">-pathmap (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="dda10-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="dda10-103">**-Pathmap** derleyici seçeneği, fiziksel yolların derleyicinin çıkış kaynak yol adlarına nasıl eşlendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dda10-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="dda10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dda10-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="dda10-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dda10-105">Arguments</span></span>

 <span data-ttu-id="dda10-106">`path1`Geçerli ortamdaki kaynak dosyalarının tam yolu</span><span class="sxs-lookup"><span data-stu-id="dda10-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="dda10-107">`sourcePath1`Her çıkış dosyasında yerine `path1` geçen kaynak yol.</span><span class="sxs-lookup"><span data-stu-id="dda10-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="dda10-108">Birden çok eşlenmiş kaynak yolunu belirtmek için, her biri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="dda10-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="dda10-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dda10-109">Remarks</span></span>

<span data-ttu-id="dda10-110">Derleyici, kaynak yolunu aşağıdaki nedenlerden dolayı çıktısına yazar:</span><span class="sxs-lookup"><span data-stu-id="dda10-110">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="dda10-111">İsteğe bağlı bir parametreye uygulandığında kaynak yolu bir bağımsız değişken <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="dda10-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="dda10-112">Kaynak yolu bir PDB dosyasına katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="dda10-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="dda10-113">PDB dosyasının yolu bir PE (taşınabilir yürütülebilir) dosyasına katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="dda10-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="dda10-114">Bu seçenek, derleyicinin çalıştığı makinedeki her fiziksel yolu, çıktı dosyalarında yazılması gereken karşılık gelen bir yola eşler.</span><span class="sxs-lookup"><span data-stu-id="dda10-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="dda10-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="dda10-115">Example</span></span>

<span data-ttu-id="dda10-116">`t.cs` **C:\\iştestlerinde\\** derleyin ve bu dizini çıktıda **\publish** ile eşleyin:</span><span class="sxs-lookup"><span data-stu-id="dda10-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="dda10-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dda10-117">See also</span></span>

- [<span data-ttu-id="dda10-118">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="dda10-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="dda10-119">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="dda10-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
