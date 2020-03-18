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
ms.openlocfilehash: 39f02c4c2e060c4be40002a2f48b0da31004a9ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606202"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="23d75-102">-win32res (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="23d75-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="23d75-103">**-win32res** seçeneği, çıktı dosyasına bir Win32 kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="23d75-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d75-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23d75-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="23d75-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="23d75-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="23d75-106">Çıktı dosyanıza eklemek istediğiniz kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="23d75-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23d75-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23d75-107">Remarks</span></span>  
 <span data-ttu-id="23d75-108">[Kaynak Derleyicisi](../../language-reference/compiler-options/resource-compiler-option.md)ile Win32 kaynak dosyası oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="23d75-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="23d75-109">Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="23d75-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="23d75-110">Win32 kaynağı, Dosya Gezgini'nde uygulamanızı tanımlamaya yardımcı olacak sürüm veya bitmap (simge) bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="23d75-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="23d75-111">**-win32res**belirtmezseniz, derleyici derleme sürümüne dayalı sürüm bilgileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23d75-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="23d75-112">[Bkz.-linkresource](./linkresource-compiler-option.md) (başvuru için) veya [-kaynak](./resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="23d75-112">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="23d75-113">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="23d75-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="23d75-114">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="23d75-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="23d75-115">**Uygulama** özelliği sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="23d75-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="23d75-116">**Kaynak Dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="23d75-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23d75-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="23d75-117">Example</span></span>  
 <span data-ttu-id="23d75-118">Oluşturmak `in.cs` için win32 kaynak `rf.res` dosyasını `in.exe`derle ve ekle:</span><span class="sxs-lookup"><span data-stu-id="23d75-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="23d75-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23d75-119">See also</span></span>

- [<span data-ttu-id="23d75-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="23d75-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="23d75-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="23d75-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
