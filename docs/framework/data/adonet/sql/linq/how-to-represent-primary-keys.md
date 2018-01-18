---
title: "Nasıl yapılır: birincil anahtarlar temsil eder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c832b7c54ecbd1f4c4a3bebcbf7f293b9a45e46c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="42298-102">Nasıl yapılır: birincil anahtarlar temsil eder</span><span class="sxs-lookup"><span data-stu-id="42298-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="42298-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özellikte <xref:System.Data.Linq.Mapping.ColumnAttribute> bir özellik veya alan bir veritabanı sütununa birincil anahtarını temsil eden atamak özniteliği.</span><span class="sxs-lookup"><span data-stu-id="42298-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="42298-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="42298-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="42298-105">Hesaplanan sütunlar birincil anahtarlar olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="42298-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="42298-106">Bir özellik veya alan birincil anahtarı olarak belirtmek için</span><span class="sxs-lookup"><span data-stu-id="42298-106">To designate a property or field as a primary key</span></span>  
  
1.  <span data-ttu-id="42298-107">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="42298-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="42298-108">Değer olarak belirtin `true`.</span><span class="sxs-lookup"><span data-stu-id="42298-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42298-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42298-109">See Also</span></span>  
 [<span data-ttu-id="42298-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="42298-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="42298-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="42298-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
