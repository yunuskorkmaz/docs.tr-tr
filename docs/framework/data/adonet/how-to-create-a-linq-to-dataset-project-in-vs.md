---
title: Visual Studio 'da LINQ to DataSet projesi oluşturma
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 91032766248b11e51b90aa788b1c64c140347c25
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802020"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="7dd3f-102">Nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7dd3f-102">How to: Create a LINQ to DataSet project in Visual Studio</span></span>

<span data-ttu-id="7dd3f-103">Farklı LINQ Projesi türleri arasında bazı derleme başvuruları ve içeri aktarılan ad alanları (Visual Basic) veya [](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri (C#) kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="7dd3f-104">LINQ için en düşük gereksinim, *System. Core. dll* ve <xref:System.Linq>için bir `using` yönergesine başvurudur.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="7dd3f-105">Bu gereksinimler, Visual Studio 2017 veya sonraki bir sürümde yeni C# bir konsol uygulama projesi oluşturursanız varsayılan olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017 or a later version.</span></span> <span data-ttu-id="7dd3f-106">Bir projeyi Visual Studio 'nun önceki bir sürümünden yükseltiyorsanız, bu LINQ ile ilgili başvuruları el ile sağlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="7dd3f-107">LINQ to DataSet, *System. Data. dll* ve *System. Data. Datase, sions. dll*' ye iki ek başvuru gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="7dd3f-108">Bir komut isteminden derleme yapıyorsanız,%ProgramFiles%\Reference, bir LINQ ile ilgili DLL 'Leri/ *Vn\microsoft\framework\v3.5*içinde el ile başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="7dd3f-109">LINQ to DataSet işlevselliği etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="7dd3f-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="7dd3f-110">Mevcut bir projede LINQ to DataSet işlevselliği etkinleştirmek için bu adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="7dd3f-111">**System. Core**, **System. Data**ve **System. Data. datasecımsions**'e başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="7dd3f-112">**Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="7dd3f-113">**Başvuru Yöneticisi** iletişim kutusunda, **System. Core**, **System. Data**ve **System. Data. Datasecccccdentitysions öğelerini**seçin.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="7dd3f-114">Seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-114">Select **OK**.</span></span>

1. <span data-ttu-id="7dd3f-115">**System. Data** ve **System. LINQ**için [using](../../../csharp/language-reference/keywords/using-directive.md) yönergelerini (veya Visual Basic [deyimlerini içeri aktarır](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="7dd3f-116">İsteğe bağlı olarak, veritabanına nasıl bağlandığınıza bağlı olarak **System. Data. Common** veya **System. Data. SqlClient**için `using` yönergesini (veya `Imports` bildirisini) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="7dd3f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd3f-117">See also</span></span>

- [<span data-ttu-id="7dd3f-118">LINQ to DataSet kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="7dd3f-118">Get started with LINQ to DataSet</span></span>](getting-started-linq-to-dataset.md)
