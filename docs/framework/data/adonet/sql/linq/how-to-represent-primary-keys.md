---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: birincil anahtarları temsil etme'
title: 'Nasıl yapılır: Birincil Anahtarları Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 1fbac2d60bd730718b5330bfd48910a61deae15c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723614"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="945ac-103">Nasıl yapılır: Birincil Anahtarları Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="945ac-103">How to: Represent Primary Keys</span></span>

<span data-ttu-id="945ac-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> Bir veritabanı sütunu için birincil anahtarı temsil etmek üzere bir özellik veya alan belirlemek için özniteliğinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="945ac-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="945ac-105">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> ..</span><span class="sxs-lookup"><span data-stu-id="945ac-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="945ac-106">, hesaplanan sütunları birincil anahtar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="945ac-106">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="945ac-107">Bir özelliği veya alanı birincil anahtar olarak belirlemek için</span><span class="sxs-lookup"><span data-stu-id="945ac-107">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="945ac-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="945ac-108">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="945ac-109">Değeri olarak belirtin `true` .</span><span class="sxs-lookup"><span data-stu-id="945ac-109">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="945ac-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="945ac-110">See also</span></span>

- [<span data-ttu-id="945ac-111">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="945ac-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="945ac-112">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="945ac-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
