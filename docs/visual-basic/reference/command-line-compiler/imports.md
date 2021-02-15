---
description: Daha fazla bilgi edinin:-Imports (Visual Basic)
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 8c6744ff857a15da9362b724a62fcf053e9fd8f0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470206"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="bebb9-103">-içeri aktarmalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bebb9-103">-imports (Visual Basic)</span></span>

<span data-ttu-id="bebb9-104">Belirtilen bir derlemeden ad alanlarını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="bebb9-104">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bebb9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bebb9-105">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="bebb9-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="bebb9-106">Arguments</span></span>  
  
|<span data-ttu-id="bebb9-107">Terim</span><span class="sxs-lookup"><span data-stu-id="bebb9-107">Term</span></span>|<span data-ttu-id="bebb9-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="bebb9-108">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="bebb9-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bebb9-109">Required.</span></span> <span data-ttu-id="bebb9-110">İçeri aktarılacak ad alanlarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="bebb9-110">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bebb9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bebb9-111">Remarks</span></span>  

 <span data-ttu-id="bebb9-112">`-imports`Seçeneği, geçerli kaynak dosyaları kümesi içinde veya başvurulan herhangi bir derlemeden tanımlanmış herhangi bir ad alanını içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="bebb9-112">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="bebb9-113">İle belirtilen bir ad alanındaki Üyeler, `-imports` derlemedeki tüm kaynak kodu dosyaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bebb9-113">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="bebb9-114">Tek kaynak kodu dosyasında bir ad alanı kullanmak için [Imports ifadesini (.net ad alanı ve türü)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="bebb9-114">Use the [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="bebb9-115">Visual Studio tümleşik geliştirme ortamında ayarlama-içeri aktarmalar</span><span class="sxs-lookup"><span data-stu-id="bebb9-115">To set -imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="bebb9-116">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bebb9-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bebb9-117">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bebb9-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="bebb9-118">2. **Başvurular** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bebb9-118">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="bebb9-119">3. ad alanı adını **Kullanıcı Içeri aktarma Ekle** düğmesinin yanındaki kutuya girin.</span><span class="sxs-lookup"><span data-stu-id="bebb9-119">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="bebb9-120">4. **Kullanıcı Içeri aktarma Ekle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bebb9-120">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bebb9-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="bebb9-121">Example</span></span>  

 <span data-ttu-id="bebb9-122">Aşağıdaki kod, belirtildiğinde derlenir `-imports:system.globalization` .</span><span class="sxs-lookup"><span data-stu-id="bebb9-122">The following code compiles when `-imports:system.globalization` is specified.</span></span> <span data-ttu-id="bebb9-123">Bu olmadan, başarılı derleme `Imports System.Globalization` kaynak kodu dosyasının başına bir deyimin dahil edilmesini veya özelliğin tam olarak nitelenmesini gerektirir `System.Globalization.CultureInfo.CurrentCulture.Name` .</span><span class="sxs-lookup"><span data-stu-id="bebb9-123">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="bebb9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bebb9-124">See also</span></span>

- [<span data-ttu-id="bebb9-125">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="bebb9-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="bebb9-126">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="bebb9-126">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="bebb9-127">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="bebb9-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
