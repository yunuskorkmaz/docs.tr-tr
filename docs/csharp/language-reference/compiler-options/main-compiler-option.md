---
title: -main (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2df02200578979f9a613f43dc92cc9e7b0cb430e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212426"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="c2d36-102">-main (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="c2d36-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="c2d36-103">Birden fazla sınıf içeriyorsa bu seçenek, giriş içeren sınıf noktası programına belirtir bir **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2d36-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d36-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2d36-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="c2d36-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c2d36-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="c2d36-106">İçeren tür **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2d36-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2d36-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2d36-107">Remarks</span></span>  
 <span data-ttu-id="c2d36-108">Birden fazla türü ile derlemeniz içeriyorsa, bir [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi, hangi türünü içeren belirtebilirsiniz **ana** programa giriş noktası olarak kullanmak istediğiniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2d36-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="c2d36-109">Bu seçenek, bir .exe dosyası derlerken kullanımı içindir.</span><span class="sxs-lookup"><span data-stu-id="c2d36-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c2d36-110">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c2d36-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c2d36-111">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="c2d36-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="c2d36-112">Tıklatın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="c2d36-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="c2d36-113">Değiştirme **Başlangıç nesnesi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="c2d36-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="c2d36-114">Bu derleyici seçeneği programlı olarak ayarlamak için bkz: <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2d36-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2d36-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2d36-115">Example</span></span>  
 <span data-ttu-id="c2d36-116">Derleme `t2.cs` ve `t3.cs`, belirtme, **ana** yöntemi bulunan `Test2`:</span><span class="sxs-lookup"><span data-stu-id="c2d36-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2d36-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2d36-117">See Also</span></span>  
 [<span data-ttu-id="c2d36-118">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="c2d36-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="c2d36-119">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="c2d36-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
