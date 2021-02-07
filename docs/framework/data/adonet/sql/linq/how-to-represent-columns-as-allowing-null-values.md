---
description: 'Daha fazla bilgi edinin: nasıl yapılır: sütunları, null değerlere Izin verecek şekilde temsil etme'
title: 'Nasıl yapılır: Sütunları Null Değerlere İzin Verecek Şekilde Temsil Etme'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 019affd13fa9c2629c6a0ec66c42f19842a4d824
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695911"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="602e5-103">Nasıl yapılır: Sütunları Null Değerlere İzin Verecek Şekilde Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="602e5-103">How to: Represent Columns as Allowing Null Values</span></span>

<span data-ttu-id="602e5-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> İlişkili veritabanı sütununun null değerleri tutabilmek için özniteliğinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="602e5-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="602e5-105">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> ..</span><span class="sxs-lookup"><span data-stu-id="602e5-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="602e5-106">Bir sütunu null değerlere izin verecek şekilde belirlemek için</span><span class="sxs-lookup"><span data-stu-id="602e5-106">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="602e5-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="602e5-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="602e5-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>Özellik değerini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="602e5-108">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="602e5-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="602e5-109">See also</span></span>

- [<span data-ttu-id="602e5-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="602e5-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="602e5-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="602e5-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
