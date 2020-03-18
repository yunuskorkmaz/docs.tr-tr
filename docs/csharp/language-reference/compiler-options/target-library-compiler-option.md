---
title: -hedef:kütüphane (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606399"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="b177f-102">-hedef:kütüphane (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="b177f-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="b177f-103">**-hedef:kitaplık** seçeneği derleyicinin yürütülebilir bir dosya (EXE) yerine dinamik bağlantı kitaplığı (DLL) oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b177f-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b177f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b177f-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="b177f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b177f-105">Remarks</span></span>  
 <span data-ttu-id="b177f-106">DLL .dll uzantısı ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b177f-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="b177f-107">[-out](./out-compiler-option.md) seçeneğinde aksi belirtilmedikçe, çıktı dosyası adı ilk giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="b177f-107">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="b177f-108">Komut satırında belirtildiğinde, .dll dosyasını oluşturmak için bir sonraki **-out** veya **-target:module** seçeneğine kadar tüm dosyalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b177f-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="b177f-109">Bir .dll dosyası [yaparken, Bir Ana](../../programming-guide/main-and-command-args/index.md) yöntem gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="b177f-109">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b177f-110">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b177f-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="b177f-111">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="b177f-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="b177f-112">**Uygulama** özelliği sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b177f-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="b177f-113">Çıktı **türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b177f-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="b177f-114">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A></span><span class="sxs-lookup"><span data-stu-id="b177f-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b177f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b177f-115">Example</span></span>  
 <span data-ttu-id="b177f-116">Derlemek `in.cs`, `in.dll`oluşturma :</span><span class="sxs-lookup"><span data-stu-id="b177f-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b177f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b177f-117">See also</span></span>

- [<span data-ttu-id="b177f-118">-hedef (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="b177f-118">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="b177f-119">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b177f-119">C# Compiler Options</span></span>](./index.md)
