---
title: "Nasıl yapılır: hangi üyeleri eşzamanlılık çakışmalar için test edildiğini belirtin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6c13c5d6578f27155b87744ed8730f5fae2e1e25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="fa16e-102">Nasıl yapılır: hangi üyeleri eşzamanlılık çakışmalar için test edildiğini belirtin</span><span class="sxs-lookup"><span data-stu-id="fa16e-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="fa16e-103">Üç numaralandırmaları biri geçerli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliği bir <xref:System.Data.Linq.Mapping.ColumnAttribute> olan üyeleri güncelleştirmede dahil edileceğini belirlemek için öznitelik iyimser eşzamanlılık çakışma algılaması için denetler.</span><span class="sxs-lookup"><span data-stu-id="fa16e-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="fa16e-104"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (Tasarım zamanında eşlenen) özelliği, eşzamanlılık çalışma zamanı özellikleri ile birlikte kullanılır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa16e-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="fa16e-105">Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fa16e-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa16e-106">Hiç üye olarak tasarlanmış sürece özgün üye değerlerinin geçerli veritabanı durumu ile karşılaştırılır `IsVersion=true`.</span><span class="sxs-lookup"><span data-stu-id="fa16e-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="fa16e-107">Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa16e-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="fa16e-108">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa16e-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="fa16e-109">Her zaman bu üye çakışmaları algılamak için kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fa16e-109">To always use this member for detecting conflicts</span></span>  
  
1.  <span data-ttu-id="fa16e-110">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa16e-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="fa16e-111">Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özellik değerine `Always`.</span><span class="sxs-lookup"><span data-stu-id="fa16e-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="fa16e-112">Hiçbir zaman bu üye çakışmaları algılamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa16e-112">To never use this member for detecting conflicts</span></span>  
  
1.  <span data-ttu-id="fa16e-113">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa16e-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="fa16e-114">Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özellik değerine `Never`.</span><span class="sxs-lookup"><span data-stu-id="fa16e-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="fa16e-115">Bu üye, yalnızca uygulama üyesinin değerini değiştiğinde çakışmaları algılamak için kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fa16e-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1.  <span data-ttu-id="fa16e-116">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa16e-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="fa16e-117">Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özellik değerine `WhenChanged`.</span><span class="sxs-lookup"><span data-stu-id="fa16e-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa16e-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa16e-118">Example</span></span>  
 <span data-ttu-id="fa16e-119">Aşağıdaki örnek belirleyen `HomePage` nesneleri hiçbir zaman test sırasında güncelleştirme denetler.</span><span class="sxs-lookup"><span data-stu-id="fa16e-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="fa16e-120">Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa16e-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fa16e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa16e-121">See Also</span></span>  
 [<span data-ttu-id="fa16e-122">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="fa16e-122">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="fa16e-123">Sağlama ve veri değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="fa16e-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
