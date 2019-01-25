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
ms.openlocfilehash: 36e5f10a61711e3245fa4b69dc583f4bb78e55e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558594"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="5fdc6-102">-main (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5fdc6-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="5fdc6-103">Birden fazla sınıf içeriyorsa, bu seçenek, giriş içeren sınıf noktası program belirtir bir **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fdc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fdc6-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="5fdc6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5fdc6-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="5fdc6-106">İçeren tür **ana** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="5fdc6-107">Belirtilen sınıf adı, tam olarak nitelenmiş olmalıdır; Bu sınıf adından önce gelen sınıfını içeren tam ad alanı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="5fdc6-108">Örneğin, `Main` yöntemi içinde bulunan `Program` sınıfını `MyApplication.Core` ad alanı, derleyici seçeneği sahip olacak şekilde `-main:MyApplication.Core.Program`.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="5fdc6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fdc6-109">Remarks</span></span>  
 <span data-ttu-id="5fdc6-110">Derlemeniz ile birden fazla tür içeriyorsa bir [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi, hangi tür içeren belirtebilirsiniz **ana** programa giriş noktası olarak kullanmak istediğiniz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-110">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="5fdc6-111">Bu seçenek, bir .exe dosyası derlenirken kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5fdc6-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5fdc6-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="5fdc6-113">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="5fdc6-114">Tıklayın **uygulama** özellik sayfası.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="5fdc6-115">Değiştirme **Başlangıç nesnesi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="5fdc6-116">Bu derleyici seçeneğini program üzerinden ayarlamak için bkz: <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fdc6-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fdc6-117">Example</span></span>  
 <span data-ttu-id="5fdc6-118">Derleme `t2.cs` ve `t3.cs`, belirtilmesi, **ana** yöntemi bulunan `Test2`:</span><span class="sxs-lookup"><span data-stu-id="5fdc6-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fdc6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fdc6-119">See also</span></span>

- [<span data-ttu-id="5fdc6-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5fdc6-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="5fdc6-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="5fdc6-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
