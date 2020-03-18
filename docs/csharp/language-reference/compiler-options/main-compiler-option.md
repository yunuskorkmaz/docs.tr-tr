---
title: -ana (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602728"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="230c8-102">-ana (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="230c8-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="230c8-103">Bu seçenek, birden fazla sınıf **bir Ana** yöntem içeriyorsa, programa giriş noktası içeren sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="230c8-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="230c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="230c8-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="230c8-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="230c8-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="230c8-106">**Ana** yöntemi içeren tür.</span><span class="sxs-lookup"><span data-stu-id="230c8-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="230c8-107">Verilen sınıf adı tam nitelikli olmalıdır; sınıfı içeren tam ad alanını içermelidir ve ardından sınıf adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="230c8-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="230c8-108">Örneğin, `Main` yöntem `Program` `MyApplication.Core` ad alanında sınıfın içinde bulunduğunda, derleyici seçeneği . `-main:MyApplication.Core.Program`</span><span class="sxs-lookup"><span data-stu-id="230c8-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="230c8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="230c8-109">Remarks</span></span>  
 <span data-ttu-id="230c8-110">Derlemeniz [Ana](../../programming-guide/main-and-command-args/index.md) yönteme sahip birden fazla tür içeriyorsa, programa giriş noktası olarak kullanmak istediğiniz **Ana** yöntemi hangi türde içerdiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="230c8-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="230c8-111">Bu seçenek, bir .exe dosyası derlenirken kullanım içindir.</span><span class="sxs-lookup"><span data-stu-id="230c8-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="230c8-112">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="230c8-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="230c8-113">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="230c8-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="230c8-114">**Uygulama** özelliği sayfasını tıklatın.</span><span class="sxs-lookup"><span data-stu-id="230c8-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="230c8-115">Başlangıç **nesnesi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="230c8-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="230c8-116">Bu derleyici seçeneğini programlı olarak <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>ayarlamak için bkz.</span><span class="sxs-lookup"><span data-stu-id="230c8-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="230c8-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="230c8-117">Example</span></span>  
 <span data-ttu-id="230c8-118">Derleme `t2.cs` ve `t3.cs`, **Ana** yöntem in `Test2`bulunacağını belirten:</span><span class="sxs-lookup"><span data-stu-id="230c8-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="230c8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="230c8-119">See also</span></span>

- [<span data-ttu-id="230c8-120">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="230c8-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="230c8-121">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="230c8-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
