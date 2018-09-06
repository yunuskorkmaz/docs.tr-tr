---
title: -(C# Derleyici Seçenekleri) en iyi duruma getirme
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
ms.openlocfilehash: f8fec2c4da49aa6cac2f8dc1dc9b07c5864b837a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43744005"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="40a25-102">-(C# Derleyici Seçenekleri) en iyi duruma getirme</span><span class="sxs-lookup"><span data-stu-id="40a25-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="40a25-103">**-En iyi duruma getirme** seçeneğini etkinleştirir veya çıkış dosyanızı daha küçük, daha hızlı ve daha verimli yapmak için derleyici tarafından gerçekleştirilen iyileştirmeleri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="40a25-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40a25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40a25-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="40a25-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40a25-105">Remarks</span></span>  
 <span data-ttu-id="40a25-106">**-en iyi duruma getirme** zamanında kodu en iyi duruma getirmek için ortak dil çalışma zamanı da bildirir.</span><span class="sxs-lookup"><span data-stu-id="40a25-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="40a25-107">Varsayılan olarak, en iyi duruma getirme devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="40a25-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="40a25-108">Belirtin **-en iyi duruma getirme +** iyileştirmeleri etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="40a25-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="40a25-109">Bir derleme tarafından kullanılacak bir modül oluşturulurken, aynı kullanın **-en iyi duruma getirme** derleme olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="40a25-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="40a25-110">**-o** öğesinin kısa biçimidir **-en iyi duruma getirme**.</span><span class="sxs-lookup"><span data-stu-id="40a25-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="40a25-111">Birleştirmek mümkündür **-en iyi duruma getirme** ve [-hata ayıklama](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="40a25-111">It is possible to combine the **-optimize** and [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="40a25-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="40a25-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="40a25-113">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="40a25-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="40a25-114">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="40a25-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="40a25-115">Değiştirme **kodu İyileştir** özelliği.</span><span class="sxs-lookup"><span data-stu-id="40a25-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="40a25-116">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="40a25-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a25-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="40a25-117">Example</span></span>  
 <span data-ttu-id="40a25-118">Derleme `t2.cs` ve derleyici iyileştirmelerini etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="40a25-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="40a25-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40a25-119">See Also</span></span>  

- [<span data-ttu-id="40a25-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="40a25-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="40a25-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="40a25-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
