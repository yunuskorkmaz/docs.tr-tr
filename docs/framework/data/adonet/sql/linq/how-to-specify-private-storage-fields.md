---
title: 'Nasıl yapılır: Özel Depolama Alanları Belirtme'
ms.date: 03/30/2017
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
ms.openlocfilehash: e6e6a4e28fbfb327f25874844f28bcbafa6d2805
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793210"
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="b09ea-102">Nasıl yapılır: Özel Depolama Alanları Belirtme</span><span class="sxs-lookup"><span data-stu-id="b09ea-102">How to: Specify Private Storage Fields</span></span>
<span data-ttu-id="b09ea-103">Temel bir depolama alanının adını <xref:System.Data.Linq.Mapping.DataAttribute> belirlemek için özniteliğinde özelliğinikullanın.<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b09ea-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="b09ea-104">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="b09ea-104">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="b09ea-105">Temel alınan bir depolama alanının adını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="b09ea-105">To specify the name of an underlying storage field</span></span>  
  
1. <span data-ttu-id="b09ea-106"><xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b09ea-106">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="b09ea-107"><xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> Özelliğin değeri olarak alanın adını atayın.</span><span class="sxs-lookup"><span data-stu-id="b09ea-107">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b09ea-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b09ea-108">See also</span></span>

- [<span data-ttu-id="b09ea-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="b09ea-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b09ea-110">Nasıl yapılır: Kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b09ea-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
