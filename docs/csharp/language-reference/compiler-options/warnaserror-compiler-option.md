---
title: "-warnaserror (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0127f8982d4b8c487a7e243025052e3eb9a5ff75
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="30d75-102">-warnaserror (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="30d75-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="30d75-103">**- Warnaserror +** seçeneği tüm uyarıları hata olarak kabul eder</span><span class="sxs-lookup"><span data-stu-id="30d75-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30d75-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30d75-104">Syntax</span></span>  
  
```console  
-warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="30d75-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30d75-105">Remarks</span></span>  
 <span data-ttu-id="30d75-106">Uyarıları hata olarak bunun yerine bildirilir ve yapı işlemi olarak normalde bildirilen herhangi bir iletisi (çıktı dosyaları oluşturulur) işlemi durduruldu.</span><span class="sxs-lookup"><span data-stu-id="30d75-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="30d75-107">Varsayılan olarak, **- warnaserror-** bir çıkış dosyasının oluşturulmasını önlemek değil uyarıları neden olur, etkilidir.</span><span class="sxs-lookup"><span data-stu-id="30d75-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="30d75-108">**-warnaserror**, aynı olduğu **- warnaserror +**, hata olarak kabul edilmesi uyarıları oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="30d75-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="30d75-109">İsteğe bağlı olarak, hata olarak kabul edilmesi için yalnızca birkaç belirli uyarıları istiyorsanız, hata olarak değerlendirmek için uyarı numaralarını virgülle ayrılmış bir listesini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="30d75-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="30d75-110">Kullanım [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) Derleyicinin görüntülemesini istediğiniz uyarı düzeyini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="30d75-110">Use [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="30d75-111">Kullanım [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) belirli uyarıları devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="30d75-111">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="30d75-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="30d75-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="30d75-113">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="30d75-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="30d75-114">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="30d75-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="30d75-115">Değiştirme **uyarıları hata olarak kabul** özelliği.</span><span class="sxs-lookup"><span data-stu-id="30d75-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
     <span data-ttu-id="30d75-116">Bu derleyici seçeneği programlı olarak ayarlamak için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="30d75-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30d75-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="30d75-117">Example</span></span>  
 <span data-ttu-id="30d75-118">Derleme `in.cs` ve derleyici hiçbir Uyarıları görüntüle:</span><span class="sxs-lookup"><span data-stu-id="30d75-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="30d75-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30d75-119">See Also</span></span>  
 [<span data-ttu-id="30d75-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="30d75-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="30d75-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="30d75-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
