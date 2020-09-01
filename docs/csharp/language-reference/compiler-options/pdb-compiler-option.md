---
description: -pdb (C# derleyici seçenekleri)
title: -pdb (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 0dcafd0fd260488922c74a2330b312e80467e779
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124922"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="b3578-103">-pdb (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="b3578-103">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="b3578-104">**-Pdb** derleyici seçeneği, hata ayıklama sembolleri dosyasının adını ve konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3578-104">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3578-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b3578-105">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="b3578-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b3578-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="b3578-107">Hata ayıklama sembolleri dosyasının adı ve konumu.</span><span class="sxs-lookup"><span data-stu-id="b3578-107">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3578-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3578-108">Remarks</span></span>  
 <span data-ttu-id="b3578-109">[-Debug (C# derleyici seçenekleri)](./debug-compiler-option.md)belirttiğinizde, derleyici aynı dizinde bir. pdb dosyası oluşturur ve bu, derleyicinin çıkış dosyasını (. exe veya. dll), çıktı dosyasının adı ile aynı olan bir dosya adıyla oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="b3578-109">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="b3578-110">**-pdb** ,. pdb dosyası için varsayılan olmayan bir dosya adı ve konum belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b3578-110">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="b3578-111">Bu derleyici seçeneği Visual Studio geliştirme ortamında ayarlanamaz veya program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="b3578-111">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3578-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3578-112">Example</span></span>  
 <span data-ttu-id="b3578-113">`t.cs`TT. pdb adlı bir. pdb dosyası derleyin ve oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b3578-113">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3578-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3578-114">See also</span></span>

- [<span data-ttu-id="b3578-115">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b3578-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b3578-116">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="b3578-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
