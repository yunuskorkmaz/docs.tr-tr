---
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
ms.openlocfilehash: 39f02c4c2e060c4be40002a2f48b0da31004a9ae
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606202"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="4dc0f-102">-win32res (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4dc0f-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="4dc0f-103">**-Win32res** seçeneği çıkış dosyasına bir Win32 kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4dc0f-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="4dc0f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4dc0f-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="4dc0f-106">Çıkış dosyanıza eklemek istediğiniz kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dc0f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4dc0f-107">Remarks</span></span>  
 <span data-ttu-id="4dc0f-108">[Kaynak derleyicisi](../../language-reference/compiler-options/resource-compiler-option.md)Ile bir Win32 kaynak dosyası oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="4dc0f-109">Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="4dc0f-110">Bir Win32 kaynağı, uygulamanızı dosya Gezgini 'nde tanımlamanızı sağlayacak sürüm veya bit eşlem (simge) bilgilerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="4dc0f-111">**-Win32res**belirtmezseniz, derleyici derleme sürümünü temel alan sürüm bilgilerini oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="4dc0f-112">Bir .NET Framework kaynak dosyası için bkz. [-linkresource](./linkresource-compiler-option.md) (başvuruya) veya [-Resource](./resource-compiler-option.md) (iliştirilecek).</span><span class="sxs-lookup"><span data-stu-id="4dc0f-112">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4dc0f-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="4dc0f-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="4dc0f-114">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="4dc0f-115">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="4dc0f-116">**Kaynak dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dc0f-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="4dc0f-117">Example</span></span>  
 <span data-ttu-id="4dc0f-118">`rf.res` Üretmek `in.cs` için`in.exe`bir Win32 kaynak dosyası derleyin ve ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4dc0f-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4dc0f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dc0f-119">See also</span></span>

- [<span data-ttu-id="4dc0f-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="4dc0f-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4dc0f-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="4dc0f-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
