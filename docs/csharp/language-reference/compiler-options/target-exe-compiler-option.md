---
title: -hedef:exe (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606459"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="fa490-102">-hedef:exe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="fa490-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="fa490-103">**-target:exe** seçeneği derleyicinin çalıştırılabilir (EXE), konsol uygulaması oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fa490-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa490-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa490-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="fa490-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa490-105">Remarks</span></span>  
 <span data-ttu-id="fa490-106">**-target:exe** seçeneği varsayılan olarak geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fa490-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="fa490-107">Çalıştırılabilir dosya .exe uzantısı ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa490-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="fa490-108">Çalıştırılabilir bir Windows programı oluşturmak için [-target:winexe'yi](./target-winexe-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa490-108">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="fa490-109">[-out](./out-compiler-option.md) seçeneğinde aksi belirtilmedikçe, çıktı dosyası adı [Ana](../../programming-guide/main-and-command-args/index.md) yöntemi içeren giriş dosyasının adını alır.</span><span class="sxs-lookup"><span data-stu-id="fa490-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="fa490-110">Komut satırında belirtildiğinde, .exe dosyasını oluşturmak için bir sonraki **-out** veya **-target:module** seçeneğine kadar tüm dosyalar kullanılır</span><span class="sxs-lookup"><span data-stu-id="fa490-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="fa490-111">.exe dosyasında derlenen kaynak kod dosyalarında bir ve tek bir **Ana** yöntem gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fa490-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="fa490-112">[-ana](./main-compiler-option.md) derleyici seçeneği, kodunuzun **Ana** yöntemle birden fazla sınıfa sahip olduğu durumlarda, hangi sınıfın **Ana** yöntemi içerdiğini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa490-112">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fa490-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fa490-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="fa490-114">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="fa490-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="fa490-115">**Uygulama** özelliği sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="fa490-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="fa490-116">Çıktı **türü** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fa490-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="fa490-117">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A></span><span class="sxs-lookup"><span data-stu-id="fa490-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa490-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa490-118">Example</span></span>  
 <span data-ttu-id="fa490-119">Aşağıdaki komut satırlarının her `in.cs`biri `in.exe`derlenecek , oluşturma:</span><span class="sxs-lookup"><span data-stu-id="fa490-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa490-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa490-120">See also</span></span>

- [<span data-ttu-id="fa490-121">-hedef (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="fa490-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="fa490-122">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fa490-122">C# Compiler Options</span></span>](./index.md)
