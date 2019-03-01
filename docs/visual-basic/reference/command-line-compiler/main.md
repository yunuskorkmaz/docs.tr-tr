---
title: -Ana
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: e1e636da1d277f80f58268b24b69802006eb8315
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966287"
---
# <a name="-main"></a><span data-ttu-id="dafa5-102">-Ana</span><span class="sxs-lookup"><span data-stu-id="dafa5-102">-main</span></span>
<span data-ttu-id="dafa5-103">Sınıf veya içeren modül belirtir `Sub Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="dafa5-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dafa5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dafa5-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="dafa5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dafa5-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="dafa5-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="dafa5-106">Required.</span></span> <span data-ttu-id="dafa5-107">Sınıf veya içeren modül adını `Sub Main` yordamı, program başladığında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="dafa5-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="dafa5-108">Bu biçiminde olabilir **-main: Modül** veya **-main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="dafa5-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dafa5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dafa5-109">Remarks</span></span>  
 <span data-ttu-id="dafa5-110">Bir yürütülebilir dosya ya da Windows yürütülebilir program oluşturduğunuzda bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="dafa5-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="dafa5-111">Varsa **-ana** seçeneği atlanırsa, derleyici için geçerli paylaşılan arar `Sub Main` tüm ortak sınıfları ve modüller.</span><span class="sxs-lookup"><span data-stu-id="dafa5-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="dafa5-112">Bkz: [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md) çeşitli türleri, bir irdelemesi `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="dafa5-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="dafa5-113">Zaman `location` devralan bir sınıf olan <xref:System.Windows.Forms.Form>, derleyici varsayılan bir ıloggerfactory sağlar `Main` sınıfı Hayır ise, uygulama başladığında yordamı `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="dafa5-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="dafa5-114">Bu, kodu geliştirme ortamında oluşturulmuş komut satırında derleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="dafa5-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="dafa5-115">-Ana Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="dafa5-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="dafa5-116">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="dafa5-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="dafa5-117">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dafa5-117">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="dafa5-118">Tıklayın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="dafa5-118">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="dafa5-119">Emin **etkinleştir uygulama çerçevesi** onay kutusu işaretli değildir.</span><span class="sxs-lookup"><span data-stu-id="dafa5-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="dafa5-120">Değer değiştirme **Başlangıç nesnesi** kutusu.</span><span class="sxs-lookup"><span data-stu-id="dafa5-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dafa5-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="dafa5-121">Example</span></span>  
 <span data-ttu-id="dafa5-122">Aşağıdaki kod derlenir `T2.vb` ve `T3.vb`, belirtilmesi, `Sub Main` yordamı bulunan `Test2` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dafa5-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="dafa5-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dafa5-123">See also</span></span>
- [<span data-ttu-id="dafa5-124">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="dafa5-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="dafa5-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dafa5-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="dafa5-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="dafa5-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="dafa5-127">Visual Basic'de ana yordam</span><span class="sxs-lookup"><span data-stu-id="dafa5-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
