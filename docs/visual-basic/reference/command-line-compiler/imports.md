---
title: -içeri aktarmalar (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 929e24a1ffd02d4e21ab1b925ddd59050b5d3cc4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005566"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="d33de-102">-içeri aktarmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d33de-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="d33de-103">Belirtilen bir derlemeden ad alanlarını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="d33de-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d33de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d33de-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="d33de-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d33de-105">Arguments</span></span>  
  
|<span data-ttu-id="d33de-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d33de-106">Term</span></span>|<span data-ttu-id="d33de-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d33de-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="d33de-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d33de-108">Required.</span></span> <span data-ttu-id="d33de-109">İçeri aktarılacak ad alanlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="d33de-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d33de-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d33de-110">Remarks</span></span>  
 <span data-ttu-id="d33de-111">@No__t-0 seçeneği, geçerli kaynak dosyaları kümesi içinde veya başvurulan herhangi bir derlemeden tanımlanmış herhangi bir ad alanını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="d33de-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="d33de-112">@No__t-0 ile belirtilen bir ad alanındaki Üyeler, derlemedeki tüm kaynak kodu dosyaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d33de-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="d33de-113">Tek kaynak kodu dosyasında bir ad alanı kullanmak için [Imports ifadesini (.net ad alanı ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="d33de-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="d33de-114">Visual Studio tümleşik geliştirme ortamında/Imports ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d33de-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d33de-115">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d33de-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d33de-116">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d33de-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d33de-117">2. **Başvurular** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d33de-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="d33de-118">3. ad alanı adını **Kullanıcı Içeri aktarma Ekle** düğmesinin yanındaki kutuya girin.</span><span class="sxs-lookup"><span data-stu-id="d33de-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="d33de-119">4. **Kullanıcı Içeri aktarma Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d33de-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d33de-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="d33de-120">Example</span></span>  
 <span data-ttu-id="d33de-121">Aşağıdaki kod `/imports:system.globalization` belirtildiğinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="d33de-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="d33de-122">Bu olmadan başarılı derleme, kaynak kodu dosyasının başına `Imports System.Globalization` ifadesinin eklenmesini veya özelliğin tam olarak `System.Globalization.CultureInfo.CurrentCulture.Name` olarak nitelenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d33de-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="d33de-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d33de-123">See also</span></span>

- [<span data-ttu-id="d33de-124">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d33de-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d33de-125">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="d33de-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="d33de-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d33de-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
