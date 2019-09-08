---
title: 'Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793493"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="ff1e9-102">Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="ff1e9-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="ff1e9-103">Veritabanı zaman damgalarını veya sürüm <xref:System.Data.Linq.Mapping.ColumnAttribute> numaralarını tutan bir veritabanı sütununu temsil eden bir alanı veya özelliği belirlemek için özniteliğinin özelliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff1e9-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="ff1e9-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff1e9-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="ff1e9-105">Bir alan veya özelliği bir zaman damgasını veya sürüm sütununu temsil edecek şekilde belirlemek için</span><span class="sxs-lookup"><span data-stu-id="ff1e9-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="ff1e9-106"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ff1e9-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="ff1e9-107">Özellik değerini olarak `true`ayarlayın. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A></span><span class="sxs-lookup"><span data-stu-id="ff1e9-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff1e9-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff1e9-108">See also</span></span>

- [<span data-ttu-id="ff1e9-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="ff1e9-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ff1e9-110">Nasıl yapılır: Eşzamanlılık çakışmaları için hangi üyelerin test edildiğini belirtin</span><span class="sxs-lookup"><span data-stu-id="ff1e9-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="ff1e9-111">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ff1e9-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
