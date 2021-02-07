---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sütunları zaman damgası veya sürüm sütunları olarak temsil etme'
title: 'Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 042e6a62c66b3f1ef522453157560e5e4c0f7de6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712512"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="904f6-103">Nasıl yapılır: Sütunları Zaman Damgası veya Sürüm Sütunları Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="904f6-103">How to: Represent Columns as Timestamp or Version Columns</span></span>

<span data-ttu-id="904f6-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> Veritabanı zaman damgalarını veya sürüm numaralarını tutan bir veritabanı sütununu temsil eden bir alanı veya özelliği belirlemek için özniteliğinin özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="904f6-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="904f6-105">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> ..</span><span class="sxs-lookup"><span data-stu-id="904f6-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="904f6-106">Bir alan veya özelliği bir zaman damgasını veya sürüm sütununu temsil edecek şekilde belirlemek için</span><span class="sxs-lookup"><span data-stu-id="904f6-106">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="904f6-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="904f6-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="904f6-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>Özellik değerini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="904f6-108">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904f6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="904f6-109">See also</span></span>

- [<span data-ttu-id="904f6-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="904f6-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="904f6-111">Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="904f6-111">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="904f6-112">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="904f6-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
