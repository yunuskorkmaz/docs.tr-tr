---
title: -Main (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602728"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="53dbe-102">-Main (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="53dbe-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="53dbe-103">Bu seçenek, birden fazla sınıf bir **Main** yöntemi içeriyorsa programa giriş noktasını içeren sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="53dbe-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53dbe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53dbe-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="53dbe-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="53dbe-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="53dbe-106">**Main** metodunu içeren tür.</span><span class="sxs-lookup"><span data-stu-id="53dbe-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="53dbe-107">Belirtilen sınıf adı tam olarak nitelenmiş olmalıdır; sınıfını içeren tam ad alanını ve ardından sınıf adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="53dbe-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="53dbe-108">Örneğin, `Main` yöntemi `MyApplication.Core` ad alanındaki `Program` sınıfının içindeyse, derleyici seçeneğinin olması gerekir `-main:MyApplication.Core.Program`.</span><span class="sxs-lookup"><span data-stu-id="53dbe-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="53dbe-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53dbe-109">Remarks</span></span>  
 <span data-ttu-id="53dbe-110">Derlemeniz bir [ana](../../programming-guide/main-and-command-args/index.md) yöntemle birden fazla tür içeriyorsa, programa giriş noktası olarak kullanmak istediğiniz **ana** yöntemi içeren türü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53dbe-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="53dbe-111">Bu seçenek bir. exe dosyası derlenirken kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="53dbe-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="53dbe-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="53dbe-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="53dbe-113">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="53dbe-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="53dbe-114">**Uygulama** Özellik sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="53dbe-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="53dbe-115">**Başlangıç nesnesi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="53dbe-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="53dbe-116">Bu derleyici seçeneğini program aracılığıyla ayarlamak için, <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>bkz.</span><span class="sxs-lookup"><span data-stu-id="53dbe-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53dbe-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="53dbe-117">Example</span></span>  
 <span data-ttu-id="53dbe-118">Ve `t2.cs` 'de`Test2`Main yönteminin bulunduğunu belirterek derleyin: `t3.cs`</span><span class="sxs-lookup"><span data-stu-id="53dbe-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="53dbe-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53dbe-119">See also</span></span>

- [<span data-ttu-id="53dbe-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="53dbe-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="53dbe-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="53dbe-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
