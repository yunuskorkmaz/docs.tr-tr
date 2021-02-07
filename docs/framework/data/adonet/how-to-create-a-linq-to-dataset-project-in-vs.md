---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma"
title: Visual Studio 'da LINQ to DataSet projesi oluşturma
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 4ab626ddaa27780759df95462faac366be8beeff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723835"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="82d23-103">Nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="82d23-103">How to: Create a LINQ to DataSet project in Visual Studio</span></span>

<span data-ttu-id="82d23-104">Farklı LINQ Projesi türleri arasında bazı derleme başvuruları ve içeri aktarılan ad alanları (Visual Basic [) veya yönergeler](../../../csharp/language-reference/keywords/using-directive.md) (C#) gerekir.</span><span class="sxs-lookup"><span data-stu-id="82d23-104">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="82d23-105">LINQ için en düşük gereksinim, *System.Core.dll* bir başvurudur ve için bir `using` yönergedir <xref:System.Linq> .</span><span class="sxs-lookup"><span data-stu-id="82d23-105">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="82d23-106">Bu gereksinimler, Visual Studio 2017 veya sonraki bir sürümde yeni bir C# konsol uygulaması projesi oluşturduğunuzda varsayılan olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="82d23-106">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017 or a later version.</span></span> <span data-ttu-id="82d23-107">Bir projeyi Visual Studio 'nun önceki bir sürümünden yükseltiyorsanız, bu LINQ ile ilgili başvuruları el ile sağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="82d23-107">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="82d23-108">LINQ to DataSet *System.Data.dll* ve *System.Data.DataSetExtensions.dll* için iki ek başvuru gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82d23-108">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="82d23-109">Bir komut isteminden derleme yapıyorsanız,%ProgramFiles%\Reference, bir LINQ ile ilgili DLL 'Leri/ *Vn\microsoft\framework\v3.5* içinde el ile başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="82d23-109">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="82d23-110">LINQ to DataSet işlevselliği etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="82d23-110">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="82d23-111">Mevcut bir projede LINQ to DataSet işlevselliği etkinleştirmek için bu adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="82d23-111">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="82d23-112">**System. Core**, **System. Data** ve **System. Data. datasecımsions**'e başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82d23-112">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="82d23-113">**Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="82d23-113">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="82d23-114">**Başvuru Yöneticisi** iletişim kutusunda, **System. Core**, **System. Data** ve **System. Data. Datasecccccdentitysions öğelerini** seçin.</span><span class="sxs-lookup"><span data-stu-id="82d23-114">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="82d23-115">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="82d23-115">Select **OK**.</span></span>

1. <span data-ttu-id="82d23-116">**System. Data** ve **System. LINQ** için [using](../../../csharp/language-reference/keywords/using-directive.md) yönergelerini (veya Visual Basic [deyimlerini içeri aktarır](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82d23-116">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="82d23-117">İsteğe bağlı olarak, `using` `Imports` veritabanına nasıl bağlandığınıza bağlı olarak **System. Data. Common** veya **System. Data. SqlClient** için bir yönerge (veya bildiri) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82d23-117">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="82d23-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82d23-118">See also</span></span>

- [<span data-ttu-id="82d23-119">LINQ to DataSet kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="82d23-119">Get started with LINQ to DataSet</span></span>](getting-started-linq-to-dataset.md)
