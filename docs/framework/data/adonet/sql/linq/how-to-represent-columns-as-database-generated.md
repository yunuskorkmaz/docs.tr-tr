---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sütunları Database-Generated olarak temsil etme'
title: 'Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 01828ef3f73257d20023168f0ea471ee7e3863c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695638"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="3eb29-103">Nasıl yapılır: Sütunları Veritabanında Oluşturulmuş Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="3eb29-103">How to: Represent Columns as Database-Generated</span></span>

<span data-ttu-id="3eb29-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> Bir alan veya özelliği veritabanı tarafından oluşturulan bir sütunu temsil edecek şekilde belirlemek için özniteliğinde özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3eb29-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="3eb29-105">Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> ..</span><span class="sxs-lookup"><span data-stu-id="3eb29-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="3eb29-106">Bir alanı veya özelliği veritabanı tarafından oluşturulan bir sütunu temsil edecek şekilde belirlemek için</span><span class="sxs-lookup"><span data-stu-id="3eb29-106">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="3eb29-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3eb29-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="3eb29-108">Özellik değerini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="3eb29-108">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb29-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eb29-109">See also</span></span>

- [<span data-ttu-id="3eb29-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="3eb29-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="3eb29-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="3eb29-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
