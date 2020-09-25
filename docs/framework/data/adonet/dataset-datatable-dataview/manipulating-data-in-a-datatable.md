---
title: DataTable Verilerini Düzenleme
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 3f98832b4aa9361346d06830f2f004fa374222ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201336"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="fa570-102">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="fa570-102">Manipulating Data in a DataTable</span></span>

<span data-ttu-id="fa570-103">Bir içinde bir oluşturduktan sonra <xref:System.Data.DataTable> <xref:System.Data.DataSet> , veritabanında bir tablo kullanırken yaptığınız aynı etkinlikleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa570-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="fa570-104">Tablodaki verileri ekleyebilir, görüntüleyebilir, düzenleyebilir ve silebilirsiniz; hataları ve olayları izleyebilirsiniz; ve tablodaki verileri sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa570-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="fa570-105">**DataTable**'daki verileri değiştirirken, değişikliklerin doğru olup olmadığını da doğrulayabilirsiniz ve değişiklikleri programlı olarak kabul edip reddetmeyeceğinizi belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa570-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa570-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fa570-106">In This Section</span></span>  

 [<span data-ttu-id="fa570-107">DataTable’a Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="fa570-107">Adding Data to a DataTable</span></span>](adding-data-to-a-datatable.md)  
 <span data-ttu-id="fa570-108">Yeni satırlar oluşturmayı ve bunları bir tabloya eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="fa570-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="fa570-109">DataTable’daki Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="fa570-109">Viewing Data in a DataTable</span></span>](viewing-data-in-a-datatable.md)  
 <span data-ttu-id="fa570-110">Verilerin orijinal ve güncel sürümleri dahil olmak üzere bir satırdaki verilere nasıl erişebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="fa570-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="fa570-111">Load Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa570-111">The Load Method</span></span>](the-load-method.md)  
 <span data-ttu-id="fa570-112">DataTable ile bir **DataTable** dolgusu için **Load** yönteminin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="fa570-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="fa570-113">DataTable Düzenlemeleri</span><span class="sxs-lookup"><span data-stu-id="fa570-113">DataTable Edits</span></span>](datatable-edits.md)  
 <span data-ttu-id="fa570-114">Önerilen değişiklikler doğrulanana ve kabul edilene kadar bir satırdaki değişiklikleri askıya alma dahil olmak üzere, bir satırdaki verilerin nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fa570-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="fa570-115">Satır Durumları ve Satır Sürümleri</span><span class="sxs-lookup"><span data-stu-id="fa570-115">Row States and Row Versions</span></span>](row-states-and-row-versions.md)  
 <span data-ttu-id="fa570-116">Bir satırın farklı durumlarıyla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa570-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="fa570-117">DataRow Silme</span><span class="sxs-lookup"><span data-stu-id="fa570-117">DataRow Deletion</span></span>](datarow-deletion.md)  
 <span data-ttu-id="fa570-118">Tablodaki bir satırın nasıl kaldırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="fa570-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="fa570-119">Satır Hatası Bilgileri</span><span class="sxs-lookup"><span data-stu-id="fa570-119">Row Error Information</span></span>](row-error-information.md)  
 <span data-ttu-id="fa570-120">Bir uygulama içindeki verilerle ilgili sorunları çözmeye yardımcı olmak için, her satır için hata bilgilerinin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fa570-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="fa570-121">AcceptChanges ve RejectChanges</span><span class="sxs-lookup"><span data-stu-id="fa570-121">AcceptChanges and RejectChanges</span></span>](acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="fa570-122">Bir satıra yapılan değişikliklerin nasıl kabul edileceği veya reddedileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="fa570-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa570-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa570-123">See also</span></span>

- [<span data-ttu-id="fa570-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="fa570-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="fa570-125">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="fa570-125">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="fa570-126">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa570-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
