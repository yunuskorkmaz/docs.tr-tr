---
title: -optimize (C# Derleyici Seçenekleri)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606604"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="93590-102">-optimize (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="93590-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="93590-103">**-optimize etme** seçeneği, çıktı dosyanızı daha küçük, daha hızlı ve daha verimli hale getirmek için derleyici tarafından gerçekleştirilen optimizasyonları sağlar veya devre dışı eder.</span><span class="sxs-lookup"><span data-stu-id="93590-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93590-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93590-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="93590-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93590-105">Remarks</span></span>  
 <span data-ttu-id="93590-106">**-en iyi duruma getirme,** aynı zamanda kodu çalışma zamanında en iyi duruma getirmek için ortak dil çalışma zamanını da bildirir.</span><span class="sxs-lookup"><span data-stu-id="93590-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="93590-107">Varsayılan olarak, optimizasyonlar devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="93590-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="93590-108">Optimizasyonları etkinleştirmek için **-optimize+** belirtin.</span><span class="sxs-lookup"><span data-stu-id="93590-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="93590-109">Bir derleme tarafından kullanılacak bir modül oluştururken, derlemenin ayarlarıyla aynı **optimize ayarları** kullanın.</span><span class="sxs-lookup"><span data-stu-id="93590-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="93590-110">**-o** **-optimize**kısa şeklidir.</span><span class="sxs-lookup"><span data-stu-id="93590-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="93590-111">**-en iyi duruma getirme** ve [hata ayıklama](./debug-compiler-option.md) seçeneklerini birleştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="93590-111">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="93590-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="93590-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="93590-113">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="93590-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="93590-114">Özellik **Oluştur** sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="93590-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="93590-115">Optimize **Kodu** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="93590-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="93590-116">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A></span><span class="sxs-lookup"><span data-stu-id="93590-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93590-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="93590-117">Example</span></span>  
 <span data-ttu-id="93590-118">Derleyici `t2.cs` optimizasyonlarını derle ve etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="93590-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="93590-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93590-119">See also</span></span>

- [<span data-ttu-id="93590-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="93590-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="93590-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="93590-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
