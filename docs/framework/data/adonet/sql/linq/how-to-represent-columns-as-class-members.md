---
title: 'Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: e73b017b5a500a8c48b3fe22557f6c6619f3b227
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166358"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="a8fc8-102">Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="a8fc8-102">How to: Represent Columns as Class Members</span></span>

<span data-ttu-id="a8fc8-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> Bir alanı veya özelliği bir veritabanı sütunuyla ilişkilendirmek için özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="a8fc8-104">Bir alanı veya özelliği bir veritabanı sütunuyla eşlemek için</span><span class="sxs-lookup"><span data-stu-id="a8fc8-104">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="a8fc8-105"><xref:System.Data.Linq.Mapping.ColumnAttribute>Özniteliği özellik veya alan bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8fc8-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8fc8-106">Example</span></span>  

 <span data-ttu-id="a8fc8-107">Aşağıdaki kod, `CustomerID` `Customer` sınıfındaki alanını `CustomerID` `Customers` veritabanı tablosundaki sütunuyla eşler.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="a8fc8-108"><xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>Ad çıkarsancan özelliğini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="a8fc8-109">Bir ad belirtmezseniz, ad, özellik veya alanla aynı ada sahip olacak şekilde adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8fc8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8fc8-110">See also</span></span>

- [<span data-ttu-id="a8fc8-111">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="a8fc8-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a8fc8-112">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a8fc8-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
