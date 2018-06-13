---
title: 'Nasıl yapılır: veritabanı adları belirtin'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a69fa1723c0660d3c6dfa8bfa7ec3b9e4dc75d7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361591"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="a4630-102">Nasıl yapılır: veritabanı adları belirtin</span><span class="sxs-lookup"><span data-stu-id="a4630-102">How to: Specify Database Names</span></span>
<span data-ttu-id="a4630-103">Kullanım <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özelliği bir <xref:System.Data.Linq.Mapping.DatabaseAttribute> özniteliği bir ad, bağlantı tarafından sağlanmayan olduğunda bir veritabanının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="a4630-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="a4630-104">Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="a4630-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="a4630-105">Veritabanının adını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="a4630-105">To specify the name of the database</span></span>  
  
1.  <span data-ttu-id="a4630-106">Ekleme <xref:System.Data.Linq.Mapping.DatabaseAttribute> veritabanı için sınıf bildirimi özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a4630-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2.  <span data-ttu-id="a4630-107">Ekleme <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özelliğine <xref:System.Data.Linq.Mapping.DatabaseAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a4630-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="a4630-108">Ayarlama <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> özellik değeri belirtmek istediğiniz adı.</span><span class="sxs-lookup"><span data-stu-id="a4630-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4630-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4630-109">See Also</span></span>  
 [<span data-ttu-id="a4630-110">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="a4630-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="a4630-111">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a4630-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
