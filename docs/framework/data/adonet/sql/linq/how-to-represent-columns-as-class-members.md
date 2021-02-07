---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sütunları sınıf üyeleri olarak temsil etme'
title: 'Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 81c35060298cde0081d040f1f874728c23d9c8ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695781"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="b2154-103">Nasıl yapılır: Sütunları Sınıf Üyesi Olarak Temsil Etme</span><span class="sxs-lookup"><span data-stu-id="b2154-103">How to: Represent Columns as Class Members</span></span>

<span data-ttu-id="b2154-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> Bir alanı veya özelliği bir veritabanı sütunuyla ilişkilendirmek için özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2154-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="b2154-105">Bir alanı veya özelliği bir veritabanı sütunuyla eşlemek için</span><span class="sxs-lookup"><span data-stu-id="b2154-105">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="b2154-106"><xref:System.Data.Linq.Mapping.ColumnAttribute>Özniteliği özellik veya alan bildirimine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b2154-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2154-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2154-107">Example</span></span>  

 <span data-ttu-id="b2154-108">Aşağıdaki kod, `CustomerID` `Customer` sınıfındaki alanını `CustomerID` `Customers` veritabanı tablosundaki sütunuyla eşler.</span><span class="sxs-lookup"><span data-stu-id="b2154-108">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="b2154-109"><xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>Ad çıkarsancan özelliğini belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b2154-109">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="b2154-110">Bir ad belirtmezseniz, ad, özellik veya alanla aynı ada sahip olacak şekilde adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b2154-110">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2154-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2154-111">See also</span></span>

- [<span data-ttu-id="b2154-112">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="b2154-112">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b2154-113">Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b2154-113">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
