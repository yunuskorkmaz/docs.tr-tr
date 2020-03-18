---
title: -yol haritası (C# Derleyici Seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606634"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="99e39-102">-yol haritası (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="99e39-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="99e39-103">**-pathmap** derleyici seçeneği, derleyici tarafından kaynak yol adları çıktısı için fiziksel yolların nasıl eşlenecek olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="99e39-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="99e39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99e39-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="99e39-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="99e39-105">Arguments</span></span>

 <span data-ttu-id="99e39-106">`path1`Geçerli ortamdaki kaynak dosyalara tam yol</span><span class="sxs-lookup"><span data-stu-id="99e39-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="99e39-107">`sourcePath1`Kaynak yolu herhangi `path1` bir çıktı dosyalarında yerine geçer.</span><span class="sxs-lookup"><span data-stu-id="99e39-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="99e39-108">Birden çok eşlenen kaynak yolu belirtmek için, her biri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="99e39-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="99e39-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99e39-109">Remarks</span></span>

<span data-ttu-id="99e39-110">Derleyici kaynak yolu çıktısına aşağıdaki nedenlerden dolayı yazar:</span><span class="sxs-lookup"><span data-stu-id="99e39-110">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="99e39-111">Kaynak yol, isteğe bağlı bir <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> parametreye uygulandığında bir bağımsız değişkenle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="99e39-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="99e39-112">Kaynak yol bir PDB dosyasına katıştırılmış.</span><span class="sxs-lookup"><span data-stu-id="99e39-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="99e39-113">PDB dosyasının yolu pe (taşınabilir çalıştırılabilir) dosyaya katıştırılır.</span><span class="sxs-lookup"><span data-stu-id="99e39-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="99e39-114">Bu seçenek, derleyicinin çıktı dosyalarına yazılması gereken karşılık gelen bir yola çalıştığı makinedeki her fiziksel yolu eşler.</span><span class="sxs-lookup"><span data-stu-id="99e39-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="99e39-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="99e39-115">Example</span></span>

<span data-ttu-id="99e39-116">C `t.cs` dizinini derle: **\\\\çalışma testleri** ve **\çıktıda yayımlamak** için dizini eşle:</span><span class="sxs-lookup"><span data-stu-id="99e39-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="99e39-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99e39-117">See also</span></span>

- [<span data-ttu-id="99e39-118">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="99e39-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="99e39-119">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="99e39-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
