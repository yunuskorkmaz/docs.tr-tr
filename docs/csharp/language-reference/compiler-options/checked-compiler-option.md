---
title: -checked (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: cf6fa0e87654d0f9d61f34ea9b29ad80921a5720
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401712"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="d79f7-102">-checked (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d79f7-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="d79f7-103">**-Kullanıma** seçeneği veri türü ve aralığı dışında bir değer sonuçlanır bir tamsayı aritmetik deyiminin kapsamı içinde olup olmadığını belirten bir [kullanıma](../../../csharp/language-reference/keywords/checked.md) veya [ denetlenmeyen](../../../csharp/language-reference/keywords/unchecked.md) anahtar sözcüğü, bir çalışma zamanı özel durumuna neden olur.</span><span class="sxs-lookup"><span data-stu-id="d79f7-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d79f7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d79f7-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="d79f7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d79f7-105">Remarks</span></span>  
 <span data-ttu-id="d79f7-106">Kapsamında olan bir tamsayı aritmetik deyimi bir `checked` veya `unchecked` anahtar sözcüğü etkisini tabi olmayan **-kullanıma** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d79f7-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="d79f7-107">Kapsamında olmayan bir tamsayı aritmetik deyimi, bir `checked` veya `unchecked` veri türünün aralığı dışında bir değer anahtar sözcükleri ve **-checked +** (veya **-kullanıma**) kullanılır deyimi bir özel durum çalışma zamanında neden derlemeyi.</span><span class="sxs-lookup"><span data-stu-id="d79f7-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="d79f7-108">Varsa **- checked -** kullanılan derlemede deyimi çalışma zamanında bir özel durum neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="d79f7-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="d79f7-109">Bu seçenek için varsayılan değerdir **- checked -**; taşma denetimini devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d79f7-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="d79f7-110">Büyük uygulamalar oluşturmak için kullanılan araçları bazı durumlarda, otomatik ayarlama - teslim +.</span><span class="sxs-lookup"><span data-stu-id="d79f7-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="d79f7-111">-Checked - belirterek Aracı'nın genel varsayılan geçersiz kılmak için - checked - kullanmaya yönelik bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="d79f7-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d79f7-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d79f7-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d79f7-113">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="d79f7-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="d79f7-114">Daha fazla bilgi için [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="d79f7-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="d79f7-115">Tıklayın **derleme** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="d79f7-115">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="d79f7-116">Tıklayın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d79f7-116">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="d79f7-117">Değiştirme **aritmetik taşma ve alttaşmayı denetle** özelliği.</span><span class="sxs-lookup"><span data-stu-id="d79f7-117">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="d79f7-118">Bu derleyici seçeneğini program aracılığıyla erişmek için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="d79f7-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d79f7-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d79f7-119">Example</span></span>  
 <span data-ttu-id="d79f7-120">Aşağıdaki komut `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="d79f7-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="d79f7-121">Kullanımını `-checked` komutunu dosyasındaki tüm tamsayı aritmetik ifadesi, kapsamı içinde olmadığını belirten bir `checked` veya `unchecked` anahtar sözcüğü ve bu veri türünün aralığı dışında bir değer sonuçlarında neden olan bir özel durum çalışma saat.</span><span class="sxs-lookup"><span data-stu-id="d79f7-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="d79f7-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d79f7-122">See Also</span></span>  

- [<span data-ttu-id="d79f7-123">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d79f7-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="d79f7-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="d79f7-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
