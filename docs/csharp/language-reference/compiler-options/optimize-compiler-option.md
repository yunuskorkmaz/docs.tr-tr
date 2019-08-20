---
title: -optimize (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: bec99ca582070a99fd8b734ef8a7b9e71d945488
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606604"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="795e6-102">-optimize (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="795e6-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="795e6-103">**-Optimize** seçeneği, çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirmek için derleyici tarafından gerçekleştirilen iyileştirmeleri sağlar veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="795e6-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="795e6-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="795e6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="795e6-105">Remarks</span></span>  
 <span data-ttu-id="795e6-106">**-optimize** , ortak dil çalışma zamanına kodu çalışma zamanında iyileştirmek için de bildirir.</span><span class="sxs-lookup"><span data-stu-id="795e6-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="795e6-107">Varsayılan olarak, iyileştirmeler devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="795e6-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="795e6-108">İyileştirmeleri etkinleştirmek için **-optimize +** belirtin.</span><span class="sxs-lookup"><span data-stu-id="795e6-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="795e6-109">Bir derleme tarafından kullanılacak bir modül oluştururken, derlemeden **en iyileştirme** ayarlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="795e6-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="795e6-110">**-o** , **en iyileştirme**için kısa bir formdur.</span><span class="sxs-lookup"><span data-stu-id="795e6-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="795e6-111">**-Optimize** ve [-Debug](./debug-compiler-option.md) seçeneklerini birleştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="795e6-111">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="795e6-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="795e6-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="795e6-113">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="795e6-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="795e6-114">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="795e6-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="795e6-115">**Optimizasyon kodu** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="795e6-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="795e6-116">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="795e6-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="795e6-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="795e6-117">Example</span></span>  
 <span data-ttu-id="795e6-118">Derleyici `t2.cs` iyileştirmelerini derleyin ve etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="795e6-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="795e6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="795e6-119">See also</span></span>

- [<span data-ttu-id="795e6-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="795e6-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="795e6-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="795e6-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
