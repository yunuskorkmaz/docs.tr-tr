---
title: DataTable Verilerini Düzenleme
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 83b1a4b6c0e477ac918a2bb4e454718fc58ece0b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203497"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="e7e52-102">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="e7e52-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="e7e52-103"><xref:System.Data.DataTable> Bir<xref:System.Data.DataSet>içinde bir oluşturduktan sonra, veritabanında bir tablo kullanırken yaptığınız aynı etkinlikleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7e52-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="e7e52-104">Tablodaki verileri ekleyebilir, görüntüleyebilir, düzenleyebilir ve silebilirsiniz; hataları ve olayları izleyebilirsiniz; ve tablodaki verileri sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7e52-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="e7e52-105">**DataTable**'daki verileri değiştirirken, değişikliklerin doğru olup olmadığını da doğrulayabilirsiniz ve değişiklikleri programlı olarak kabul edip reddetmeyeceğinizi belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7e52-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7e52-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e7e52-106">In This Section</span></span>  
 [<span data-ttu-id="e7e52-107">DataTable’a Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="e7e52-107">Adding Data to a DataTable</span></span>](adding-data-to-a-datatable.md)  
 <span data-ttu-id="e7e52-108">Yeni satırlar oluşturmayı ve bunları bir tabloya eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7e52-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="e7e52-109">DataTable’daki Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e7e52-109">Viewing Data in a DataTable</span></span>](viewing-data-in-a-datatable.md)  
 <span data-ttu-id="e7e52-110">Verilerin orijinal ve güncel sürümleri dahil olmak üzere bir satırdaki verilere nasıl erişebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7e52-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="e7e52-111">Load Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7e52-111">The Load Method</span></span>](the-load-method.md)  
 <span data-ttu-id="e7e52-112">DataTable ile bir **DataTable** dolgusu için **Load** yönteminin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7e52-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="e7e52-113">DataTable Düzenlemeleri</span><span class="sxs-lookup"><span data-stu-id="e7e52-113">DataTable Edits</span></span>](datatable-edits.md)  
 <span data-ttu-id="e7e52-114">Önerilen değişiklikler doğrulanana ve kabul edilene kadar bir satırdaki değişiklikleri askıya alma dahil olmak üzere, bir satırdaki verilerin nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7e52-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="e7e52-115">Satır Durumları ve Satır Sürümleri</span><span class="sxs-lookup"><span data-stu-id="e7e52-115">Row States and Row Versions</span></span>](row-states-and-row-versions.md)  
 <span data-ttu-id="e7e52-116">Bir satırın farklı durumlarıyla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7e52-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="e7e52-117">DataRow Silme</span><span class="sxs-lookup"><span data-stu-id="e7e52-117">DataRow Deletion</span></span>](datarow-deletion.md)  
 <span data-ttu-id="e7e52-118">Tablodaki bir satırın nasıl kaldırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7e52-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="e7e52-119">Satır Hatası Bilgileri</span><span class="sxs-lookup"><span data-stu-id="e7e52-119">Row Error Information</span></span>](row-error-information.md)  
 <span data-ttu-id="e7e52-120">Bir uygulama içindeki verilerle ilgili sorunları çözmeye yardımcı olmak için, her satır için hata bilgilerinin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e7e52-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="e7e52-121">AcceptChanges ve RejectChanges</span><span class="sxs-lookup"><span data-stu-id="e7e52-121">AcceptChanges and RejectChanges</span></span>](acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="e7e52-122">Bir satıra yapılan değişikliklerin nasıl kabul edileceği veya reddedileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e7e52-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e52-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7e52-123">See also</span></span>

- [<span data-ttu-id="e7e52-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="e7e52-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="e7e52-125">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="e7e52-125">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="e7e52-126">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="e7e52-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
