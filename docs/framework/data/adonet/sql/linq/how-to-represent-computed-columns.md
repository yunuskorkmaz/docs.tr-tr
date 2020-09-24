---
title: 'Nasıl yapılır: Hesaplanan Sütunları Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: d952a6c22cd96bbc89aeebfa4b13e9727a363c73
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166332"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="ac520-102">Nasıl yapılır: Hesaplanan Sütunları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="ac520-102">How to: Represent Computed Columns</span></span>

<span data-ttu-id="ac520-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> İçeriği hesaplama sonucu olan bir sütunu temsil etmek için bir özniteliğinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac520-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="ac520-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> ..</span><span class="sxs-lookup"><span data-stu-id="ac520-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="ac520-105">, hesaplanan sütunları birincil anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ac520-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="ac520-106">Hesaplanan bir sütunu göstermek için</span><span class="sxs-lookup"><span data-stu-id="ac520-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="ac520-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ac520-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="ac520-108">Özelliğe formülün dize gösterimini atayın <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> .</span><span class="sxs-lookup"><span data-stu-id="ac520-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac520-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac520-109">See also</span></span>

- [<span data-ttu-id="ac520-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="ac520-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ac520-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ac520-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
