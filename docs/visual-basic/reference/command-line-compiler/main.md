---
title: -Ana
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51a527dfddd2b78ac1c0559420298a66eb4b63f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652928"
---
# <a name="-main"></a><span data-ttu-id="b845f-102">-Ana</span><span class="sxs-lookup"><span data-stu-id="b845f-102">-main</span></span>
<span data-ttu-id="b845f-103">Sınıf veya içeren modülünü belirtir `Sub Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="b845f-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b845f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b845f-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="b845f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b845f-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="b845f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b845f-106">Required.</span></span> <span data-ttu-id="b845f-107">Sınıf veya içeren modül adını `Sub Main` program başladığında çağrılacak yordamı.</span><span class="sxs-lookup"><span data-stu-id="b845f-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="b845f-108">Bu formda olabilir **-ana: Modül** veya **-main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="b845f-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b845f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b845f-109">Remarks</span></span>  
 <span data-ttu-id="b845f-110">Bir yürütülebilir dosya veya Windows yürütülebilir program oluşturduğunuzda, bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b845f-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="b845f-111">Varsa **-ana** seçeneği atlanırsa, derleyici geçerli bir için paylaşılan arar `Sub Main` tüm ortak sınıfları ve modüller.</span><span class="sxs-lookup"><span data-stu-id="b845f-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="b845f-112">Bkz: [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md) çeşitli formlarının Tartışması için `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="b845f-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="b845f-113">Zaman `location` öğesinden devralınan bir sınıf <xref:System.Windows.Forms.Form>, varsayılan derleyici sağlar `Main` sınıfı Hayır ise, uygulama başladığında yordamı `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="b845f-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="b845f-114">Bu, komut satırında geliştirme ortamında oluşturulan kod derleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="b845f-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="b845f-115">-Visual Studio tümleşik geliştirme ortamında ana ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b845f-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="b845f-116">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="b845f-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b845f-117">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="b845f-117">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b845f-118">Tıklatın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="b845f-118">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="b845f-119">Emin olun **etkinleştir uygulama çerçevesi** onay kutusu işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="b845f-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="b845f-120">Değer değiştirme **Başlangıç nesnesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="b845f-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b845f-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b845f-121">Example</span></span>  
 <span data-ttu-id="b845f-122">Aşağıdaki kod derlerken `T2.vb` ve `T3.vb`, belirtme, `Sub Main` yordamı bulunan `Test2` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b845f-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="b845f-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b845f-123">See Also</span></span>  
 [<span data-ttu-id="b845f-124">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b845f-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b845f-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b845f-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="b845f-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b845f-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="b845f-127">Visual Basic'de ana yordam</span><span class="sxs-lookup"><span data-stu-id="b845f-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
