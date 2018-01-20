---
title: "-win32res (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c24da8bb745847612d882d00eff7f03dbc60475
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="ec61d-102">-win32res (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="ec61d-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="ec61d-103">**-Win32res** seçeneği bir Win32 kaynağı çıktı dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="ec61d-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec61d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec61d-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="ec61d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ec61d-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="ec61d-106">Çıkış dosyanızın eklemek istediğiniz kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="ec61d-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec61d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec61d-107">Remarks</span></span>  
 <span data-ttu-id="ec61d-108">Win32 kaynak dosyasını ile oluşturulan [kaynak derleyici](../../language-reference/compiler-options/resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ec61d-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="ec61d-109">Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ec61d-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="ec61d-110">Win32 kaynak sürüm içerebilir veya yardımcı olacak bit eşlem (simgesi) bilgilerini dosya Gezgini uygulamanızda belirleyin.</span><span class="sxs-lookup"><span data-stu-id="ec61d-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="ec61d-111">Belirtmezseniz, **-win32res**, derleyici derleme sürümünü temel alan sürüm bilgisini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec61d-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="ec61d-112">Bkz: [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (için başvuru) veya [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="ec61d-112">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ec61d-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ec61d-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="ec61d-114">Projenin açmak **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="ec61d-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="ec61d-115">Tıklatın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="ec61d-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="ec61d-116">Tıklayın **kaynak dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="ec61d-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec61d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec61d-117">Example</span></span>  
 <span data-ttu-id="ec61d-118">Derleme `in.cs` ve Win32 kaynak dosyası ekleme `rf.res` üretmek için `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="ec61d-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec61d-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ec61d-119">See Also</span></span>  
 [<span data-ttu-id="ec61d-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ec61d-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ec61d-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="ec61d-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
