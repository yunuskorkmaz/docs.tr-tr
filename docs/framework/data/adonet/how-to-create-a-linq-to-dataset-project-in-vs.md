---
title: Bir LINQ to DataSet projesi Visual Studio'da oluşturma
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 12544c6b5153a5f6300072d1646f2c119fb255a1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515752"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="e93e4-102">Nasıl yapılır: bir LINQ to DataSet projesi Visual Studio'da oluşturma</span><span class="sxs-lookup"><span data-stu-id="e93e4-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="e93e4-103">Belirli bütünleştirilmiş kod başvuruları ve içeri aktarılan ad alanlarını (Visual Basic) LINQ projeleri farklı türde gerektirir veya [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri (C#).</span><span class="sxs-lookup"><span data-stu-id="e93e4-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="e93e4-104">LINQ için en düşük gereksinimi başvurusudur *System.Core.dll* ve `using` yönergesi <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="e93e4-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="e93e4-105">Visual Studio 2017'de yeni bir C# konsol uygulaması projesi oluşturursanız, bu gereksinimleri varsayılan olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e93e4-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="e93e4-106">Bir projeyi Visual Studio'nun önceki bir sürümden yükseltiyorsanız, LINQ ile ilgili bu başvuruları el ile sağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e93e4-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="e93e4-107">LINQ to DataSet gerektiren iki ek başvurular *System.Data.dll* ve *System.Data.DataSetExtensions.dll*.</span><span class="sxs-lookup"><span data-stu-id="e93e4-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="e93e4-108">Bir komut istemi'nden oluşturuyorsanız, el ile LINQ ilgili DLL'leri başvurmalıdır *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span><span class="sxs-lookup"><span data-stu-id="e93e4-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="e93e4-109">LINQ DataSet işlevselliğini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e93e4-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="e93e4-110">İçin veri kümesi işlevsellik mevcut bir projeyi LINQ'i etkinleştirmek için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="e93e4-110">Follow these steps to to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="e93e4-111">Başvuruları Ekle **System.Core**, **System.Data**, ve **System.Data.DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="e93e4-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="e93e4-112">İçinde **Çözüm Gezgini**, sağ **başvuruları** düğümünü seçip alt **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e93e4-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="e93e4-113">İçinde **başvuru Yöneticisi** iletişim kutusunda **System.Core**, **System.Data**, ve **System.Data.DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="e93e4-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="e93e4-114">Seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e93e4-114">Select **OK**.</span></span>

1. <span data-ttu-id="e93e4-115">Ekleme [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri (veya [aktarır deyimleri](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) Visual Basic'te) için **System.Data** ve **System.Linq**.</span><span class="sxs-lookup"><span data-stu-id="e93e4-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="e93e4-116">İsteğe bağlı olarak, ekleme bir `using` yönergesi (veya `Imports` deyimi) için **System.Data.Common** veya **System.Data.SqlClient**veritabanına bağlandığınız nasıl bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="e93e4-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="e93e4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e93e4-117">See also</span></span>

- [<span data-ttu-id="e93e4-118">LINQ to DataSet kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="e93e4-118">Get started with LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
