---
title: -pdb (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602572"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="15ac2-102">-pdb (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="15ac2-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="15ac2-103">**-Pdb** derleyici seçeneği, hata ayıklama sembolleri dosyasının adını ve konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="15ac2-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15ac2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15ac2-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="15ac2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="15ac2-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="15ac2-106">Hata ayıklama sembolleri dosyasının adı ve konumu.</span><span class="sxs-lookup"><span data-stu-id="15ac2-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15ac2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15ac2-107">Remarks</span></span>  
 <span data-ttu-id="15ac2-108">[-Debug (C# derleyici seçenekleri)](./debug-compiler-option.md)belirttiğinizde, derleyici aynı dizinde bir. pdb dosyası oluşturur ve bu, derleyicinin çıkış dosyasını (. exe veya. dll) çıktı dosyasının adı ile aynı olan bir dosya adı ile oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="15ac2-108">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="15ac2-109">**-pdb** ,. pdb dosyası için varsayılan olmayan bir dosya adı ve konum belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="15ac2-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="15ac2-110">Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="15ac2-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15ac2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="15ac2-111">Example</span></span>  
 <span data-ttu-id="15ac2-112">TT `t.cs` . pdb adlı bir. pdb dosyası derleyin ve oluşturun:</span><span class="sxs-lookup"><span data-stu-id="15ac2-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="15ac2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15ac2-113">See also</span></span>

- [<span data-ttu-id="15ac2-114">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="15ac2-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="15ac2-115">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="15ac2-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
