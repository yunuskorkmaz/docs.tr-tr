---
title: 'Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: de7109e0fed0eb7c1975ad7360a7588ef9b294ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793147"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="64f9a-102">Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="64f9a-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="64f9a-103">İyimser eşzamanlılık çakışmalarının algılanması için güncelleştirme denetimlerinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] hangi üyelerin ekleneceğini <xref:System.Data.Linq.Mapping.ColumnAttribute> belirtmek üzere bir öznitelik üzerinde <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğe üç Numaralandırmalardan birini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="64f9a-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="64f9a-104">Özelliği (tasarım zamanında eşlenir), içindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]çalışma zamanı eşzamanlılık özellikleriyle birlikte kullanılır. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A></span><span class="sxs-lookup"><span data-stu-id="64f9a-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="64f9a-105">Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış.</span><span class="sxs-lookup"><span data-stu-id="64f9a-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64f9a-106">Özgün üye değerleri, hiçbir üye olarak `IsVersion=true`belirlenmedikçe geçerli veritabanı durumuyla karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="64f9a-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="64f9a-107">Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="64f9a-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="64f9a-108">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="64f9a-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="64f9a-109">Çakışmaları saptamak için her zaman bu üyeyi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="64f9a-109">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="64f9a-110"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="64f9a-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="64f9a-111">Özellik değerini olarak `Always`ayarlayın. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A></span><span class="sxs-lookup"><span data-stu-id="64f9a-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="64f9a-112">Çakışmaları saptamak için bu üyeyi hiçbir şekilde kullanmayın</span><span class="sxs-lookup"><span data-stu-id="64f9a-112">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="64f9a-113"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="64f9a-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="64f9a-114">Özellik değerini olarak `Never`ayarlayın. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A></span><span class="sxs-lookup"><span data-stu-id="64f9a-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="64f9a-115">Bu üyeyi yalnızca uygulama üyenin değerini değiştirdiği zaman çakışmaları saptamak için kullanmak için</span><span class="sxs-lookup"><span data-stu-id="64f9a-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="64f9a-116"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="64f9a-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="64f9a-117">Özellik değerini olarak `WhenChanged`ayarlayın. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A></span><span class="sxs-lookup"><span data-stu-id="64f9a-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64f9a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="64f9a-118">Example</span></span>  
 <span data-ttu-id="64f9a-119">Aşağıdaki örnek, güncelleştirme denetimleri `HomePage` sırasında nesnelerin hiçbir şekilde sınanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="64f9a-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="64f9a-120">Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="64f9a-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="64f9a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64f9a-121">See also</span></span>

- [<span data-ttu-id="64f9a-122">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="64f9a-122">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="64f9a-123">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="64f9a-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
