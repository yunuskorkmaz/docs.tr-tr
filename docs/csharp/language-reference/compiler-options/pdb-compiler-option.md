---
title: "-pdb (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7528283765c2b6f4a9d5e84015526a95938a6281
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="39e6e-102">-pdb (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="39e6e-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="39e6e-103">**- Pdb** derleyici seçeneği, hata ayıklama simgeleri dosyasının konumunu ve adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="39e6e-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39e6e-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="39e6e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="39e6e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="39e6e-106">Hata ayıklama simgeleri dosyasının konumunu ve adını.</span><span class="sxs-lookup"><span data-stu-id="39e6e-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39e6e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39e6e-107">Remarks</span></span>  
 <span data-ttu-id="39e6e-108">Belirttiğinizde [-debug (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), derleyici çıkış dosyasının adı ile aynı olan bir dosya adıyla derleyici çıktı dosyası (.exe veya .dll) oluşturur, bir .pdb dosyası ile aynı dizinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39e6e-108">When you specify [-debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="39e6e-109">**-pdb** varsayılan olmayan dosya adı ve .pdb dosyası için konum belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="39e6e-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="39e6e-110">Visual Studio geliştirme ortamında bu derleyici seçeneği ayarlanamaz ya da programlı olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="39e6e-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39e6e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="39e6e-111">Example</span></span>  
 <span data-ttu-id="39e6e-112">Derleme `t.cs` ve tt.pdb adlı bir .pdb dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="39e6e-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="39e6e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39e6e-113">See Also</span></span>  
 [<span data-ttu-id="39e6e-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="39e6e-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="39e6e-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="39e6e-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
