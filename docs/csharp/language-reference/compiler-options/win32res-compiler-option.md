---
title: -win32res (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 4026fcbd7dc2ef29c1e7ee01a0f37b3ff471b187
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322388"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="4f192-102">-win32res (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4f192-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="4f192-103">**-Win32res** seçeneği, çıkış dosyasında bir Win32 kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="4f192-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f192-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f192-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="4f192-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4f192-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="4f192-106">Çıkış dosyanızı eklemek istediğiniz kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="4f192-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f192-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f192-107">Remarks</span></span>  
 <span data-ttu-id="4f192-108">Bir Win32 kaynak dosyası ile oluşturulan [kaynak derleyici](../../language-reference/compiler-options/resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4f192-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="4f192-109">Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4f192-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="4f192-110">Bir Win32 kaynağı sürümü içerebilir veya yardımcı olan bit eşlem (simge) bilgilerini ve dosya Gezgini'ndeki uygulamanız belirleyin.</span><span class="sxs-lookup"><span data-stu-id="4f192-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="4f192-111">Siz belirtmezseniz **-win32res**, derleyici derleme sürümünü temel alan sürüm bilgisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f192-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="4f192-112">Bkz: [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (için başvuru) veya [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="4f192-112">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4f192-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4f192-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="4f192-114">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="4f192-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="4f192-115">Tıklayın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="4f192-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="4f192-116">Tıklayarak **kaynak dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="4f192-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f192-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f192-117">Example</span></span>  
 <span data-ttu-id="4f192-118">Derleme `in.cs` ve bir Win32 kaynak dosyası ekleme `rf.res` üretmek için `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="4f192-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f192-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f192-119">See also</span></span>

- [<span data-ttu-id="4f192-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4f192-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="4f192-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="4f192-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
