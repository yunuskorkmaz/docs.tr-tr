---
title: "-main (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a6dca6e62dbf69783babf2e16dc4e7c36c6705c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="main-c-compiler-options"></a><span data-ttu-id="591c3-102">/main (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="591c3-102">/main (C# Compiler Options)</span></span>
<span data-ttu-id="591c3-103">Birden fazla sınıf içeriyorsa bu seçenek, giriş içeren sınıf noktası programına belirtir bir **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="591c3-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="591c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="591c3-104">Syntax</span></span>  
  
```console  
/main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="591c3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="591c3-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="591c3-106">İçeren tür **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="591c3-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="591c3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="591c3-107">Remarks</span></span>  
 <span data-ttu-id="591c3-108">Birden fazla türü ile derlemeniz içeriyorsa, bir [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi, hangi türünü içeren belirtebilirsiniz **ana** programa giriş noktası olarak kullanmak istediğiniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="591c3-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="591c3-109">Bu seçenek, bir .exe dosyası derlerken kullanımı içindir.</span><span class="sxs-lookup"><span data-stu-id="591c3-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="591c3-110">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="591c3-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="591c3-111">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="591c3-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="591c3-112">Tıklatın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="591c3-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="591c3-113">Değiştirme **Başlangıç nesnesi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="591c3-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="591c3-114">Bu derleyici seçeneği programlı olarak ayarlamak için bkz: <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="591c3-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="591c3-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="591c3-115">Example</span></span>  
 <span data-ttu-id="591c3-116">Derleme `t2.cs` ve `t3.cs`, belirtme, **ana** yöntemi bulunan `Test2`:</span><span class="sxs-lookup"><span data-stu-id="591c3-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="591c3-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="591c3-117">See Also</span></span>  
 [<span data-ttu-id="591c3-118">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="591c3-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="591c3-119">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="591c3-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
