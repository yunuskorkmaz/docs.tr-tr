---
title: "Nasıl yapılır: sütunlar veritabanında oluşturulan olarak temsil eder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a0b36e7035b885985e70203146957cdfca92148b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="cede0-102">Nasıl yapılır: sütunlar veritabanında oluşturulan olarak temsil eder</span><span class="sxs-lookup"><span data-stu-id="cede0-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="cede0-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> özellikte <xref:System.Data.Linq.Mapping.ColumnAttribute> veritabanında oluşturulan bir sütun olarak temsil eden bir alan veya özellik atamak özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cede0-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="cede0-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="cede0-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="cede0-105">Bir alan veya özellik veritabanında oluşturulan bir sütunu temsil eden olarak atamak için</span><span class="sxs-lookup"><span data-stu-id="cede0-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="cede0-106">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cede0-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="cede0-107">Özellik değerini ayarlamak `true`.</span><span class="sxs-lookup"><span data-stu-id="cede0-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cede0-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cede0-108">See Also</span></span>  
 [<span data-ttu-id="cede0-109">LINQ to SQL nesne modeli</span><span class="sxs-lookup"><span data-stu-id="cede0-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="cede0-110">Nasıl yapılır: kod düzenleyicisini kullanarak sınıflar özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cede0-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
