---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 5530da4c784346df4a1088998b8d2027feee08e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403167"
---
# <a name="-main"></a><span data-ttu-id="3de5c-102">-main</span><span class="sxs-lookup"><span data-stu-id="3de5c-102">-main</span></span>
<span data-ttu-id="3de5c-103">Yordamı içeren sınıfı veya modülü belirtir `Sub Main` .</span><span class="sxs-lookup"><span data-stu-id="3de5c-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de5c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3de5c-104">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="3de5c-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="3de5c-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="3de5c-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3de5c-106">Required.</span></span> <span data-ttu-id="3de5c-107">Program başlatıldığında Çağrılacak yordamı içeren sınıfın veya modülün adı `Sub Main` .</span><span class="sxs-lookup"><span data-stu-id="3de5c-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="3de5c-108">Bu, **-Main: Module** veya **-Main: Namespace. Module**biçiminde olabilir.</span><span class="sxs-lookup"><span data-stu-id="3de5c-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3de5c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3de5c-109">Remarks</span></span>  
 <span data-ttu-id="3de5c-110">Yürütülebilir bir dosya veya Windows yürütülebilir programı oluştururken bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="3de5c-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="3de5c-111">**-Main** seçeneği atlanırsa, derleyici `Sub Main` tüm ortak sınıflarda ve modüllerde geçerli bir paylaşılan arar.</span><span class="sxs-lookup"><span data-stu-id="3de5c-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="3de5c-112">Yordamın çeşitli biçimlerinin tartışılması için [Visual Basic ana yordama](../../programming-guide/program-structure/main-procedure.md) bakın `Main` .</span><span class="sxs-lookup"><span data-stu-id="3de5c-112">See [Main Procedure in Visual Basic](../../programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="3de5c-113">Sınıfından `location` devralan bir sınıf olduğunda <xref:System.Windows.Forms.Form> , derleyici bir `Main` yordam yoksa, uygulamayı başlatan varsayılan bir yordam sağlar `Main` .</span><span class="sxs-lookup"><span data-stu-id="3de5c-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="3de5c-114">Bu, geliştirme ortamında oluşturulan komut satırında kod derlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3de5c-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="3de5c-115">Visual Studio tümleşik geliştirme ortamında Main 'i ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3de5c-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="3de5c-116">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3de5c-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3de5c-117">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3de5c-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="3de5c-118">**Uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3de5c-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="3de5c-119">**Uygulama çerçevesini etkinleştir** onay kutusunun işaretli olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="3de5c-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="3de5c-120">**Başlangıç nesnesi** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3de5c-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3de5c-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="3de5c-121">Example</span></span>  
 <span data-ttu-id="3de5c-122">Aşağıdaki kod, `T2.vb` ve `T3.vb` yordamının sınıfında bulunduğunu belirtmek için derleme `Sub Main` yapar `Test2` .</span><span class="sxs-lookup"><span data-stu-id="3de5c-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="3de5c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3de5c-123">See also</span></span>

- [<span data-ttu-id="3de5c-124">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3de5c-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3de5c-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3de5c-125">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="3de5c-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3de5c-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="3de5c-127">Visual Basic'de Ana Yordam</span><span class="sxs-lookup"><span data-stu-id="3de5c-127">Main Procedure in Visual Basic</span></span>](../../programming-guide/program-structure/main-procedure.md)
