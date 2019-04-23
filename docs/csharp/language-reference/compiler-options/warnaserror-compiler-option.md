---
title: -warnaserror (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 2ae555c2e049e687f508e62b5b46fd8a744e827f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329109"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="ec091-102">-warnaserror (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ec091-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="ec091-103">**- Warnaserror +** seçeneği, tüm uyarıları hata olarak davranır</span><span class="sxs-lookup"><span data-stu-id="ec091-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec091-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec091-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ec091-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec091-105">Remarks</span></span>  
 <span data-ttu-id="ec091-106">Uyarıları hata olarak bunun yerine bildirilir ve yapı işlemi olarak normalde bildirilebilecek herhangi bir iletiyi (çıkış dosyaları oluşturulur) durdu.</span><span class="sxs-lookup"><span data-stu-id="ec091-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="ec091-107">Varsayılan olarak, **- warnaserror-** olmayan bir çıkış dosyasının oluşturulmasını önlemek uyarılara neden aslında olduğu.</span><span class="sxs-lookup"><span data-stu-id="ec091-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="ec091-108">**-warnaserror**, aynı olduğu **- warnaserror +**, uyarıları hata olarak kabul edilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ec091-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="ec091-109">İsteğe bağlı olarak, isterseniz hata olarak kabul edilmesi için yalnızca birkaç belirli uyarıları hata olarak değerlendirilecek uyarıların virgülle ayrılmış bir listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec091-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="ec091-110">Kullanım [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) derleyici görüntülemek için istediğiniz uyarı düzeyini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="ec091-110">Use [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="ec091-111">Kullanım [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) belirli uyarıları devre dışı.</span><span class="sxs-lookup"><span data-stu-id="ec091-111">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ec091-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ec091-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ec091-113">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="ec091-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ec091-114">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="ec091-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="ec091-115">Değiştirme **uyarıları hata olarak değerlendir** özelliği.</span><span class="sxs-lookup"><span data-stu-id="ec091-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="ec091-116">Bu derleyici seçeneğini program üzerinden ayarlamak için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="ec091-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec091-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec091-117">Example</span></span>  
 <span data-ttu-id="ec091-118">Derleme `in.cs` ve derleyicinin hiçbir uyarılar:</span><span class="sxs-lookup"><span data-stu-id="ec091-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec091-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec091-119">See also</span></span>

- [<span data-ttu-id="ec091-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ec091-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="ec091-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="ec091-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
