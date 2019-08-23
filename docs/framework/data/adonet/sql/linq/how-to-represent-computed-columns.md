---
title: 'Nasıl yapılır: Hesaplanan Sütunları Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 01c3442448285893ebb476ed11889e073065d4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943540"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="7c747-102">Nasıl yapılır: Hesaplanan Sütunları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="7c747-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="7c747-103">İçeriği hesaplama sonucu olan bir <xref:System.Data.Linq.Mapping.ColumnAttribute> sütunu temsil etmek için bir özniteliğinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c747-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="7c747-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c747-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7c747-105">, hesaplanan sütunları birincil anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7c747-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="7c747-106">Hesaplanan bir sütunu göstermek için</span><span class="sxs-lookup"><span data-stu-id="7c747-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="7c747-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c747-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="7c747-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> Özelliğe formülün dize gösterimini atayın.</span><span class="sxs-lookup"><span data-stu-id="7c747-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c747-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c747-109">See also</span></span>

- [<span data-ttu-id="7c747-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="7c747-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="7c747-111">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7c747-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
