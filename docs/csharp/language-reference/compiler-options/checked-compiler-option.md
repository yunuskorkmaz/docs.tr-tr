---
title: "-checked (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0a8cc66609fe542fc7db166cd208cfcedb204b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="ae694-102">-checked (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ae694-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="ae694-103">**-İşaretli** seçeneği belirtir ve veri türü, aralığın dışında bir değer sonuçlanan bir tamsayı aritmetiği deyimi kapsamında değil olup bir [işaretli](../../../csharp/language-reference/keywords/checked.md) veya [ Unchecked](../../../csharp/language-reference/keywords/unchecked.md) anahtar sözcük, bir çalışma zamanı özel neden olur.</span><span class="sxs-lookup"><span data-stu-id="ae694-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae694-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae694-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ae694-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae694-105">Remarks</span></span>  
 <span data-ttu-id="ae694-106">Kapsamında bir tamsayı aritmetiği deyimi bir `checked` veya `unchecked` anahtar sözcüğü etkisini tabi değil **-işaretli** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ae694-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="ae694-107">Kapsamında olmayan bir tamsayı aritmetik deyim, bir `checked` veya `unchecked` anahtar sözcüğü sonuçları veri türü aralık dışında bir değer ve **-checked +** (**-işaretli**) kullanılır derleme, bu deyim bir özel durum çalışma zamanında neden olur.</span><span class="sxs-lookup"><span data-stu-id="ae694-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (**-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="ae694-108">Varsa **- işaretli -** kullanılan derlemede deyimi çalışma zamanında bir özel durum neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="ae694-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="ae694-109">Bu seçenek için varsayılan değer **- işaretli -**.</span><span class="sxs-lookup"><span data-stu-id="ae694-109">The default value for this option is **-checked-**.</span></span> <span data-ttu-id="ae694-110">Kullanmak için bir senaryo **- işaretli -** büyük uygulamalar oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="ae694-110">One scenario for using **-checked-** is in building large applications.</span></span> <span data-ttu-id="ae694-111">Bazen otomatikleştirilmiş Araçlar, bu tür uygulamalar oluşturmak için kullanılır ve böyle bir araç otomatik olarak ayarlayabilir **-işaretli** için +.</span><span class="sxs-lookup"><span data-stu-id="ae694-111">Sometimes automated tools are used to build such applications, and such a tool might automatically set **-checked** to +.</span></span> <span data-ttu-id="ae694-112">Belirterek aracın genel Varsayılanı geçersiz kılabilirsiniz **- işaretli -**.</span><span class="sxs-lookup"><span data-stu-id="ae694-112">You can override the tool's global default by specifying **-checked-**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ae694-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ae694-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="ae694-114">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="ae694-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="ae694-115">Daha fazla bilgi için bkz: [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="ae694-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="ae694-116">Tıklatın **yapı** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="ae694-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="ae694-117">Tıklatın **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ae694-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="ae694-118">Değiştirme **denetlemek için aritmetik taşma/underflow** özelliği.</span><span class="sxs-lookup"><span data-stu-id="ae694-118">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="ae694-119">Bu derleyici seçeneği programlı olarak erişmek için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae694-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae694-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae694-120">Example</span></span>  
 <span data-ttu-id="ae694-121">Aşağıdaki komut derlerken `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="ae694-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="ae694-122">Kullanımını `-checked` komutunu herhangi bir tamsayı aritmetik deyimle dosyasında, kapsamında olduğunu belirten bir `checked` veya `unchecked` anahtar sözcüğü ve bu veri türü aralık dışında bir değer sonuçlarında neden olan bir özel durum çalışma süre.</span><span class="sxs-lookup"><span data-stu-id="ae694-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae694-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae694-123">See Also</span></span>  
 [<span data-ttu-id="ae694-124">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ae694-124">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ae694-125">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="ae694-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
