---
title: -warnaserror (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 66c78ee56c9d5153b5b878b2e695ad4ee6bffe0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606259"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="b6e29-102">-warnaserror (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="b6e29-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="b6e29-103">**-Warnaserror +** seçeneği tüm uyarıları hata olarak değerlendirir</span><span class="sxs-lookup"><span data-stu-id="b6e29-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6e29-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="b6e29-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6e29-105">Remarks</span></span>  
 <span data-ttu-id="b6e29-106">Normalde uyarı olarak bildirilen tüm iletiler, bunun yerine hata olarak bildirilir ve derleme işlemi durdurulur (çıktı dosyası derlenmemiştir).</span><span class="sxs-lookup"><span data-stu-id="b6e29-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="b6e29-107">Varsayılan olarak, **-warnaserror-** , bir çıkış dosyasının oluşturulmasını engellemez uyarısı oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b6e29-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="b6e29-108">\- **warnaserror +** ile aynı olan **warnaserror**, uyarıların hata olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="b6e29-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="b6e29-109">İsteğe bağlı olarak, yalnızca birkaç özel uyarının hata olarak değerlendirilmesini istiyorsanız, hata olarak değerlendirilecek uyarı numaralarının virgülle ayrılmış bir listesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6e29-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="b6e29-110">Derleyicinin görüntülemesini istediğiniz uyarı düzeyini belirtmek için [-Warn](./warn-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6e29-110">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="b6e29-111">Belirli uyarıları devre dışı bırakmak için [-nowarn](./nowarn-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6e29-111">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b6e29-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b6e29-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="b6e29-113">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="b6e29-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="b6e29-114">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b6e29-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="b6e29-115">**Uyarıları hata olarak değerlendir** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b6e29-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="b6e29-116">Bu derleyici seçeneğini program aracılığıyla ayarlamak için, <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>bkz.</span><span class="sxs-lookup"><span data-stu-id="b6e29-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6e29-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6e29-117">Example</span></span>  
 <span data-ttu-id="b6e29-118">Derle `in.cs` ve derleyicinin hiçbir uyarı görüntülememe:</span><span class="sxs-lookup"><span data-stu-id="b6e29-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6e29-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6e29-119">See also</span></span>

- [<span data-ttu-id="b6e29-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b6e29-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b6e29-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="b6e29-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
