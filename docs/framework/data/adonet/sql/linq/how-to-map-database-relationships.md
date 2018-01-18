---
title: "Nasıl yapılır: veritabanı ilişkileri eşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b1637fd322468f743c29605b31c3c6849bd78aa6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-map-database-relationships"></a>Nasıl yapılır: veritabanı ilişkileri eşleme
Özellik varlık sınıfınızda her zaman aynı olacaktır herhangi bir veri ilişki başvuran şifreleyebilirsiniz. Northwind örnek veritabanı Örneğin, müşteriler genellikle siparişler geçirdiği için her zaman bir ilişkisi yoktur müşteriler ve bunların Siparişler arasında modelindeki.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tanımlayan bir <xref:System.Data.Linq.Mapping.AssociationAttribute> bu tür ilişkiler temsil yardımcı için öznitelik. Bu öznitelik ile birlikte kullanılan <xref:System.Data.Linq.EntitySet%601> ve <xref:System.Data.Linq.EntityRef%601> türleri bir veritabanındaki yabancı anahtar ilişkisi ne olacağını gösterir. Daha fazla bilgi için ilişki özniteliğini bölümüne bakın [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  AssociationAttribute ve ColumnAttribute depolama özellik değerleri büyük küçük harf duyarlıdır. Örneğin, öznitelikte AssociationAttribute.Storage özelliği için kullanılan değerler başka bir yerde kod içinde kullanılan karşılık gelen özellik adları söz konusu eşleştiğinden emin olun. Bu, tüm .NET programlama dili için olanlar genellikle büyük dahil olmak üzere küçük harf duyarlı, olmayan geçerlidir [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)]. Depo özelliği hakkında daha fazla bilgi için bkz: <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 Bir-çok, bu konunun ilerleyen bölümlerinde örnekte olduğu gibi çoğu ilişkisidir. Bire bir ve çok-çok ilişkileri gibi gösterebilir:  
  
-   Bire bir: Bu tür bir ilişkiyi temsil dahil ederek <xref:System.Data.Linq.EntitySet%601> her iki tarafında.  
  
     Örneğin, göz önünde bulundurun bir `Customer` - `SecurityCode` ilişki, içinde Müşteri'nin güvenlik kodu bulunamayacaktır oluşturulan `Customer` tablo ve yalnızca yetkili kişiler tarafından erişilebilir.  
  
-   Çoktan çoğa: çok-çok ilişkileri, bağlantı tablonun birincil anahtarı içinde (olarak da adlandırılan *birleşim* tablo) diğer iki tablolardaki yabancı anahtarlar bileşik tarafından oluşturulmuş.  
  
     Örneğin, göz önünde bulundurun bir `Employee` - `Project` çok-çok ilişkisi biçimlendirilmiş bağlantı tablosunu kullanarak `EmployeeProject`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]üç sınıflarını kullanarak da böyle bir ilişki modellenebilir gerektirir: `Employee`, `Project`, ve `EmployeeProject`. Bu durumda, arasındaki ilişkiyi değiştirme bir `Employee` ve `Project` birincil anahtarın bir güncelleştirme gerektiren görünebilir `EmployeeProject`. Ancak, bu durum en iyi varolan silme olarak Modellenen `EmployeeProject` ve yeni bir oluşturma `EmployeeProject`.  
  
    > [!NOTE]
    >  İlişkisel veritabanları ilişkilerde genellikle diğer tablolardaki birincil anahtarlar başvuran yabancı anahtar değerleri olarak Modellenen. Bunlar arasında gezinmek için açıkça iki tablo bir ilişkisel kullanarak ilişkilendirmenize *birleştirme* işlemi.  
    >   
    >  Veritabanındaki nesneler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], diğer el, birbirlerine özelliği başvuruları veya kullanarak gezinme başvuruları koleksiyonları kullanarak başvurmak *nokta* gösterimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir-çok, `Customer` sınıfı müşteriler ve bunların siparişler arasındaki ilişkiyi bildiren bir özelliğe sahiptir.  `Orders` Özelliği türüdür <xref:System.Data.Linq.EntitySet%601>. Bu türü bu ilişki bire çok olduğunu belirtir (birçok siparişler bir müşteriye). <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> Özelliği nasıl Bu ilişkilendirme, yani, bu biriyle Karşılaştırılacak ilgili sınıf özelliği adı belirterek yapıldığını açıklamak için kullanılır. Bu örnekte, `CustomerID` özelliği karşılaştırıldığı, yalnızca bir veritabanı *birleştirme* bu sütun değeri karşılaştırmak.  
  
> [!NOTE]
>  Kullanıyorsanız [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] sınıflar arasında bir ilişki oluşturmak için.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Örnek  
 Durum ayrıca ters çevirebilirsiniz. Yerine `Customer` müşteriler ve siparişler arasındaki ilişkiyi tanımlamak için sınıf, kullanabileceğiniz `Order` sınıfı. `Order` Sınıfını kullanan <xref:System.Data.Linq.EntityRef%601> aşağıdaki kod örneğinde olduğu gibi geri müşteriye ilişki tanımlamak için türü.  
  
> [!NOTE]
>  <xref:System.Data.Linq.EntityRef%601> Sınıf destekler *yüklenirken ertelenmiş*. Daha fazla bilgi için *bkz* [hemen yüklenirken karşı ertelenmiş](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Kod Düzenleyicisini Kullanarak Varlık Sınıflarını Özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [LINQ to SQL Nesne Modeli](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
