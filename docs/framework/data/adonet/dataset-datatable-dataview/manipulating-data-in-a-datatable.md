---
title: DataTable verilerini düzenleme
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 54ebde293dd6701b8018e77c6bf8d773a4931e2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509584"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="309ec-102">DataTable verilerini düzenleme</span><span class="sxs-lookup"><span data-stu-id="309ec-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="309ec-103">Oluşturduktan sonra bir <xref:System.Data.DataTable> içinde bir <xref:System.Data.DataSet>, bir veritabanında bir tablo kullanırken yaptığınız aynı etkinlikler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="309ec-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="309ec-104">Ekleyebilir, görüntüleyin, düzenleyin ve tablo verilerini silme; hataları ve olayları izleyebilirsiniz; ve tablodaki verileri sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="309ec-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="309ec-105">Verileri değiştirirken bir **DataTable**, değişikliklerin doğru olduğundan ve programlı olarak geçir belirlemek olup olmadığını da doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="309ec-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="309ec-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="309ec-106">In This Section</span></span>  
 [<span data-ttu-id="309ec-107">DataTable’a Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="309ec-107">Adding Data to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-data-to-a-datatable.md)  
 <span data-ttu-id="309ec-108">Yeni satırları oluşturun ve bunları bir tabloya ekleyin açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="309ec-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="309ec-109">DataTable’daki Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="309ec-109">Viewing Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/viewing-data-in-a-datatable.md)  
 <span data-ttu-id="309ec-110">Bir satırda, verilerin geçerli ve özgün sürümlerine dahil olmak üzere verilere nasıl erişileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="309ec-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="309ec-111">Load Yöntemi</span><span class="sxs-lookup"><span data-stu-id="309ec-111">The Load Method</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/the-load-method.md)  
 <span data-ttu-id="309ec-112">Kullanımını açıklar **yük** doldurmak için yöntemi bir **DataTable** satırlarla.</span><span class="sxs-lookup"><span data-stu-id="309ec-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="309ec-113">DataTable Düzenlemeleri</span><span class="sxs-lookup"><span data-stu-id="309ec-113">DataTable Edits</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-edits.md)  
 <span data-ttu-id="309ec-114">Önerilen değişiklikler doğrulandı ve kabul kadar bir satır için değişiklikleri askıya alma dahil olmak üzere, bir satırdaki verileri değiştirmek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="309ec-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="309ec-115">Satır Durumları ve Satır Sürümleri</span><span class="sxs-lookup"><span data-stu-id="309ec-115">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="309ec-116">Bir satırın farklı durumları hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="309ec-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="309ec-117">DataRow Silme</span><span class="sxs-lookup"><span data-stu-id="309ec-117">DataRow Deletion</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarow-deletion.md)  
 <span data-ttu-id="309ec-118">Tablodan bir satır kaldırmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="309ec-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="309ec-119">Satır Hatası Bilgileri</span><span class="sxs-lookup"><span data-stu-id="309ec-119">Row Error Information</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 <span data-ttu-id="309ec-120">Her bir uygulamadaki verileri sorunları çözmenize yardımcı olması için satır, hata bilgilerini nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="309ec-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="309ec-121">AcceptChanges ve RejectChanges</span><span class="sxs-lookup"><span data-stu-id="309ec-121">AcceptChanges and RejectChanges</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="309ec-122">Kabul etme veya reddetme bir satır için yapılan değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="309ec-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309ec-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="309ec-123">See also</span></span>
- [<span data-ttu-id="309ec-124">DataTables</span><span class="sxs-lookup"><span data-stu-id="309ec-124">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="309ec-125">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="309ec-125">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="309ec-126">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="309ec-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
