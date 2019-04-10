---
title: 'Nasıl yapılır: Hesaplanan Sütunları Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: df72562b303e5b9a7c31334df06926f157b59b05
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324750"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="d9af1-102">Nasıl yapılır: Hesaplanan Sütunları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="d9af1-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="d9af1-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> özelliği bir <xref:System.Data.Linq.Mapping.ColumnAttribute> hesaplamanın sonucu olan bir sütun göstermek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d9af1-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="d9af1-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9af1-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="d9af1-105">Hesaplanan sütunlar, birincil anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d9af1-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="d9af1-106">Hesaplanmış bir sütun göstermek için</span><span class="sxs-lookup"><span data-stu-id="d9af1-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="d9af1-107">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d9af1-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="d9af1-108">Formül dize gösterimini atama <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d9af1-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9af1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9af1-109">See also</span></span>

- [<span data-ttu-id="d9af1-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="d9af1-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="d9af1-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d9af1-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
