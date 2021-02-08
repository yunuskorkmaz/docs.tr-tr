---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: eşzamanlılık çakışmaları için hangi üyelerin test edildiğini belirleme'
title: 'Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: f2623c1e6afcf97ee2de62b94b80145ca2a5cad3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785867"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="078b6-103">Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="078b6-103">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>

<span data-ttu-id="078b6-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> İyimser eşzamanlılık çakışmalarının algılanması için güncelleştirme denetimlerinde hangi üyelerin ekleneceğini belirtmek üzere bir öznitelik üzerinde özelliğe üç Numaralandırmalardan birini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="078b6-104">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="078b6-105"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özelliği (tasarım zamanında eşlenir), içindeki çalışma zamanı eşzamanlılık özellikleriyle birlikte kullanılır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="078b6-105">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="078b6-106">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="078b6-106">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="078b6-107">Özgün üye değerleri, hiçbir üye olarak belirlenmedikçe geçerli veritabanı durumuyla karşılaştırılır `IsVersion=true` .</span><span class="sxs-lookup"><span data-stu-id="078b6-107">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="078b6-108">Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="078b6-108">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="078b6-109">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ..</span><span class="sxs-lookup"><span data-stu-id="078b6-109">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="078b6-110">Çakışmaları saptamak için her zaman bu üyeyi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="078b6-110">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="078b6-111"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="078b6-111">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="078b6-112"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özellik değerini olarak ayarlayın `Always` .</span><span class="sxs-lookup"><span data-stu-id="078b6-112">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="078b6-113">Çakışmaları saptamak için bu üyeyi hiçbir şekilde kullanmayın</span><span class="sxs-lookup"><span data-stu-id="078b6-113">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="078b6-114"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="078b6-114">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="078b6-115"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özellik değerini olarak ayarlayın `Never` .</span><span class="sxs-lookup"><span data-stu-id="078b6-115">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="078b6-116">Bu üyeyi yalnızca uygulama üyenin değerini değiştirdiği zaman çakışmaları saptamak için kullanmak için</span><span class="sxs-lookup"><span data-stu-id="078b6-116">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="078b6-117"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="078b6-117">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="078b6-118"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özellik değerini olarak ayarlayın `WhenChanged` .</span><span class="sxs-lookup"><span data-stu-id="078b6-118">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="078b6-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="078b6-119">Example</span></span>  

 <span data-ttu-id="078b6-120">Aşağıdaki örnek, `HomePage` güncelleştirme denetimleri sırasında nesnelerin hiçbir şekilde sınanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="078b6-120">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="078b6-121">Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="078b6-121">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="078b6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="078b6-122">See also</span></span>

- [<span data-ttu-id="078b6-123">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="078b6-123">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="078b6-124">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="078b6-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
