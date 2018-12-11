---
title: Bir LINQ to DataSet projesi Visual Studio'da oluşturma
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154040"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="dc141-102">Nasıl Yapılır: Bir LINQ to DataSet projesi Visual Studio'da oluşturma</span><span class="sxs-lookup"><span data-stu-id="dc141-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="dc141-103">Belirli bütünleştirilmiş kod başvuruları ve içeri aktarılan ad alanlarını (Visual Basic) LINQ projeleri farklı türde gerektirir veya [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri (C#).</span><span class="sxs-lookup"><span data-stu-id="dc141-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="dc141-104">LINQ için en düşük gereksinimi başvurusudur *System.Core.dll* ve `using` yönergesi <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="dc141-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="dc141-105">Visual Studio 2017'de yeni bir C# konsol uygulaması projesi oluşturursanız, bu gereksinimleri varsayılan olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dc141-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="dc141-106">Bir projeyi Visual Studio'nun önceki bir sürümden yükseltiyorsanız, LINQ ile ilgili bu başvuruları el ile sağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="dc141-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="dc141-107">LINQ to DataSet gerektiren iki ek başvurular *System.Data.dll* ve *System.Data.DataSetExtensions.dll*.</span><span class="sxs-lookup"><span data-stu-id="dc141-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="dc141-108">Bir komut istemi'nden oluşturuyorsanız, el ile LINQ ilgili DLL'leri başvurmalıdır *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span><span class="sxs-lookup"><span data-stu-id="dc141-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="dc141-109">LINQ DataSet işlevselliğini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="dc141-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="dc141-110">Varolan bir projede veri kümesi işlevine LINQ'i etkinleştirmek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="dc141-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="dc141-111">Başvuruları Ekle **System.Core**, **System.Data**, ve **System.Data.DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="dc141-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="dc141-112">İçinde **Çözüm Gezgini**, sağ **başvuruları** düğümünü seçip alt **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="dc141-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="dc141-113">İçinde **başvuru Yöneticisi** iletişim kutusunda **System.Core**, **System.Data**, ve **System.Data.DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="dc141-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="dc141-114">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dc141-114">Select **OK**.</span></span>

1. <span data-ttu-id="dc141-115">Ekleme [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri (veya [aktarır deyimleri](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic'te) için **System.Data** ve **System.Linq**.</span><span class="sxs-lookup"><span data-stu-id="dc141-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="dc141-116">İsteğe bağlı olarak, ekleme bir `using` yönergesi (veya `Imports` deyimi) için **System.Data.Common** veya **System.Data.SqlClient**veritabanına bağlandığınız nasıl bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="dc141-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc141-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc141-117">See also</span></span>

- [<span data-ttu-id="dc141-118">LINQ to DataSet kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="dc141-118">Get started with LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
