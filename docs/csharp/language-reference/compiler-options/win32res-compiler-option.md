---
description: -win32res (C# derleyici seçenekleri)
title: -win32res (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: c220c78a6d2c3109402a20f0de40fe9665d6c730
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140821"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="40e56-103">-win32res (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="40e56-103">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="40e56-104">**-Win32res** seçeneği çıkış dosyasına bir Win32 kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="40e56-104">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e56-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="40e56-105">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="40e56-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="40e56-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="40e56-107">Çıkış dosyanıza eklemek istediğiniz kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="40e56-107">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40e56-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40e56-108">Remarks</span></span>  
 <span data-ttu-id="40e56-109">[Kaynak derleyicisi](resource-compiler-option.md)Ile bir Win32 kaynak dosyası oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="40e56-109">A Win32 resource file can be created with the [Resource Compiler](resource-compiler-option.md).</span></span> <span data-ttu-id="40e56-110">Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="40e56-110">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="40e56-111">Bir Win32 kaynağı, uygulamanızı dosya Gezgini 'nde tanımlamanızı sağlayacak sürüm veya bit eşlem (simge) bilgilerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="40e56-111">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="40e56-112">**-Win32res**belirtmezseniz, derleyici derleme sürümünü temel alan sürüm bilgilerini oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="40e56-112">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="40e56-113">Bir .NET Framework kaynak dosyası için bkz. [-linkresource](./linkresource-compiler-option.md) (başvuruya) veya [-Resource](./resource-compiler-option.md) (iliştirilecek).</span><span class="sxs-lookup"><span data-stu-id="40e56-113">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="40e56-114">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="40e56-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="40e56-115">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="40e56-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="40e56-116">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="40e56-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="40e56-117">**Kaynak dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="40e56-117">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40e56-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="40e56-118">Example</span></span>  
 <span data-ttu-id="40e56-119">`in.cs`Üretmek için bir Win32 kaynak dosyası derleyin ve ekleyin `rf.res` `in.exe` :</span><span class="sxs-lookup"><span data-stu-id="40e56-119">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="40e56-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40e56-120">See also</span></span>

- [<span data-ttu-id="40e56-121">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="40e56-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="40e56-122">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="40e56-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
