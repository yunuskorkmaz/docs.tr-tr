---
title: -pdb (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: b0a566931ac76a3adb191f423a497bc446e280c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575508"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="73167-102">-pdb (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="73167-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="73167-103">**- Pdb** derleyici seçeneği, hata ayıklama sembol dosyasının konumunu ve adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73167-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73167-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73167-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="73167-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="73167-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="73167-106">Hata ayıklama sembol dosyasının konumunu ve adını.</span><span class="sxs-lookup"><span data-stu-id="73167-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73167-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73167-107">Remarks</span></span>  
 <span data-ttu-id="73167-108">Belirttiğinizde [-hata ayıklama (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), derleyici, çıkış dosyasının adı ile aynı olan bir dosya adıyla derleyici çıktı dosyası (.exe veya .dll) oluşturur burada bir .pdb dosyası ile aynı dizinde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73167-108">When you specify [-debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="73167-109">**-pdb** varsayılan olmayan dosya adı ve .pdb dosyasının konumunu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="73167-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="73167-110">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlanamaz ya da programlı olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="73167-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73167-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="73167-111">Example</span></span>  
 <span data-ttu-id="73167-112">Derleme `t.cs` ve tt.pdb adlı bir .pdb dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="73167-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="73167-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73167-113">See also</span></span>

- [<span data-ttu-id="73167-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="73167-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="73167-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="73167-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
