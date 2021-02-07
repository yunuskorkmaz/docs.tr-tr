---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: hesaplanan sütunları temsil etme'
title: 'Nasıl yapılır: Hesaplanan Sütunları Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 5f3b4898cd29c148665c6696b0b3abab42bd071c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695625"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="b76e6-103">Nasıl yapılır: Hesaplanan Sütunları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="b76e6-103">How to: Represent Computed Columns</span></span>

<span data-ttu-id="b76e6-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> İçeriği hesaplama sonucu olan bir sütunu temsil etmek için bir özniteliğinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b76e6-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="b76e6-105">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> ..</span><span class="sxs-lookup"><span data-stu-id="b76e6-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b76e6-106">, hesaplanan sütunları birincil anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b76e6-106">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="b76e6-107">Hesaplanan bir sütunu göstermek için</span><span class="sxs-lookup"><span data-stu-id="b76e6-107">To represent a computed column</span></span>  
  
1. <span data-ttu-id="b76e6-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b76e6-108">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="b76e6-109">Özelliğe formülün dize gösterimini atayın <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> .</span><span class="sxs-lookup"><span data-stu-id="b76e6-109">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b76e6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b76e6-110">See also</span></span>

- [<span data-ttu-id="b76e6-111">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="b76e6-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b76e6-112">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b76e6-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
