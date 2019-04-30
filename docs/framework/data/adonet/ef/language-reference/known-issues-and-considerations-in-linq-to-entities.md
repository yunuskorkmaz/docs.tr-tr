---
title: LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 3945d4fc92bea2c4212da0507618203603ae8aba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780553"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler
Bu bölümde ile ilgili bilinen sorunlar hakkında bilgi [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.  
  
- [LINQ sorguları, önbelleğe alınamaz](#LINQQueriesThatAreNotCached)  
  
- [Kayıp bilgileri sıralama](#OrderingInfoLost)  
  
- [İşaretsiz tamsayılar desteklenmiyor](#UnsignedIntsUnsupported)  
  
- [Tür dönüştürme hataları](#TypeConversionErrors)  
  
- [Desteklenmeyen skaler olmayan değişkenleri başvurma](#RefNonScalarClosures)  
  
- [SQL Server 2000 ile iç içe geçmiş sorgular başarısız olabilir](#NestedQueriesSQL2000)  
  
- [Anonim bir tür için yansıtma](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a>LINQ sorguları, önbelleğe alınamaz  
 .NET Framework 4.5 ile başlayarak, LINQ to Entities sorgularında otomatik olarak önbelleğe alınır. Ancak LINQ to Entities sorgularında, geçerli `Enumerable.Contains` işleci bellek içi koleksiyonlara otomatik olarak önbelleğe alınmaz. Bellek içi koleksiyonları derlenmiş LINQ sorgularında ayrıca kümesini parametreleştirme izin verilmez.  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a>Kayıp bilgileri sıralama  
 Sütunlar anonim bir tür yansıtma karşı yürütülen sorgular kaybolur sıralama bilgilerini neden olacak bir [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] veritabanı için "80" bir uyumluluk düzeyi ayarlayın.  Order by listesi bir sütun adı bir sütun adı Seçici içinde eşleştiğinde aşağıdaki örnekte gösterildiği gibi oluşur:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a>İşaretsiz tamsayılar desteklenmiyor  
 İçinde bir işaretsiz tamsayı türü belirten bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] nedeniyle sorgu desteklenmiyor [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] işaretsiz tamsayılar desteklemez. İşaretsiz bir tamsayı belirtmeniz durumunda bir <xref:System.ArgumentException> özel durumu aşağıdaki örnekte gösterildiği gibi sorgu ifade çevirisi sırasında oluşturulur. Bu örnek sorguları bir sipariş kimliği 48000 için.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a>Tür dönüştürme hataları  
 Visual Basic'te, bir özellik SQL Server bit türünde bir sütun 1'i kullanarak bir değer ile eşlendiğinde `CByte` işlevi, bir <xref:System.Data.SqlClient.SqlException> "aritmetik taşma hata" iletisi ile oluşturulur. Aşağıdaki örnek sorgularda `Product.MakeFlag` üzerinden sorgu sonuçları yinelendiğinde sütununda AdventureWorks örnek veritabanı ve bir özel durum harekete geçirilir.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a>Desteklenmeyen skaler olmayan değişkenleri başvurma  
 Bir varlıkta bir sorgu gibi bir skaler olmayan değişkenleri başvuran desteklenmiyor. Bu tür bir sorgu yürütüldüğünde, bir <xref:System.NotSupportedException> bildiren bir ileti ile özel durum oluştu "türünde bir sabit değer oluşturulamıyor `EntityType`. Yalnızca ilkel türler ('Örneğin Int32, String ve Guid') bu bağlamda desteklenir."  
  
> [!NOTE]
>  Skalar değişkenler koleksiyonunu başvuran desteklenir.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>SQL Server 2000 ile iç içe geçmiş sorgular başarısız olabilir  
 Üç veya daha fazla düzeyleri derin iç içe geçmiş Transact-SQL sorguları ürettikleri ile SQL Server 2000, LINQ to Entities sorgularında başarısız olabilir.  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a>Anonim bir tür için yansıtma  
 İlgili nesneler kullanarak eklemek için ilk sorgu yolunuzu tanımlarsanız, <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metodunda <xref:System.Data.Objects.ObjectQuery%601> ve ardından döndürülen nesneleri anonim bir tür projeye LINQ kullanmak için dahil etme yöntemi belirtilen nesnelerin sorguda yer almaz Sonuç.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 İlgili nesneler almak için döndürülen türleri anonim bir tür için proje değil.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
