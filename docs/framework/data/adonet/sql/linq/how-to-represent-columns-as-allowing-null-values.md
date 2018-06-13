---
title: 'Nasıl yapılır: sütun Null değerlere izin veren olarak temsil eder'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 6700ee5d4de53dd82da29d48ca7c42785d52afc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355983"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="19ac8-102">Nasıl yapılır: sütun Null değerlere izin veren olarak temsil eder</span><span class="sxs-lookup"><span data-stu-id="19ac8-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="19ac8-103">Kullanım [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> özellikte <xref:System.Data.Linq.Mapping.ColumnAttribute> ilişkili veritabanı sütunu null değerler tutabilir belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="19ac8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="19ac8-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="19ac8-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="19ac8-105">Bir sütun null değerlere izin veren olarak atamak için</span><span class="sxs-lookup"><span data-stu-id="19ac8-105">To designate a column as allowing null values</span></span>  
  
1.  <span data-ttu-id="19ac8-106">Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="19ac8-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="19ac8-107">Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> özellik değerine `true`.</span><span class="sxs-lookup"><span data-stu-id="19ac8-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19ac8-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19ac8-108">See Also</span></span>  
 [<span data-ttu-id="19ac8-109">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="19ac8-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="19ac8-110">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="19ac8-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
