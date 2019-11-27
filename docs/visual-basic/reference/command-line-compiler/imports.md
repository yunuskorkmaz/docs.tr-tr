---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 380e71e462f736d4564a37b83567007fa9461b05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332961"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="2d0dc-102">-içeri aktarmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d0dc-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="2d0dc-103">Belirtilen bir derlemeden ad alanlarını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d0dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d0dc-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2d0dc-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2d0dc-105">Arguments</span></span>  
  
|<span data-ttu-id="2d0dc-106">Terim</span><span class="sxs-lookup"><span data-stu-id="2d0dc-106">Term</span></span>|<span data-ttu-id="2d0dc-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="2d0dc-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="2d0dc-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-108">Required.</span></span> <span data-ttu-id="2d0dc-109">İçeri aktarılacak ad alanlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d0dc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d0dc-110">Remarks</span></span>  
 <span data-ttu-id="2d0dc-111">`-imports` seçeneği, geçerli kaynak dosyaları kümesi içinde veya başvurulan herhangi bir derlemeden tanımlanmış herhangi bir ad alanını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="2d0dc-112">`-imports` ile belirtilen bir ad alanındaki Üyeler, derlemedeki tüm kaynak kodu dosyaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="2d0dc-113">Tek kaynak kodu dosyasında bir ad alanı kullanmak için [Imports ifadesini (.net ad alanı ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="2d0dc-114">Visual Studio tümleşik geliştirme ortamında/Imports ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2d0dc-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="2d0dc-115">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2d0dc-116">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="2d0dc-117">2. **Başvurular** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="2d0dc-118">3. ad alanı adını **Kullanıcı Içeri aktarma Ekle** düğmesinin yanındaki kutuya girin.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="2d0dc-119">4. **Kullanıcı Içeri aktarma Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2d0dc-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="2d0dc-120">Example</span></span>  
 <span data-ttu-id="2d0dc-121">Aşağıdaki kod `/imports:system.globalization` belirtildiğinde derlenir.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="2d0dc-122">Bu olmadan, başarılı derleme, kaynak kodu dosyasının başına `Imports System.Globalization` bir deyimin eklenmesini veya özelliğin tam olarak `System.Globalization.CultureInfo.CurrentCulture.Name`uygun olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="2d0dc-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d0dc-123">See also</span></span>

- [<span data-ttu-id="2d0dc-124">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2d0dc-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2d0dc-125">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d0dc-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="2d0dc-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2d0dc-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
