---
title: LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 90119da0fce7a708323d790f91f28206cac0a0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150148"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler
Bu bölümde, LINQ ile Varlıklar sorguları için bilinen sorunlar hakkında bilgi sağlar.  
  
- [Önbelleğe Alınamayan LINQ Sorguları](#LINQQueriesThatAreNotCached)  
  
- [Kayıp Bilgileri Sıralama](#OrderingInfoLost)  
  
- [İmzasız Tümsatörler Desteklenmiyor](#UnsignedIntsUnsupported)  
  
- [Dönüşüm Hatalarını Yazın](#TypeConversionErrors)  
  
- [Skaler Olmayan Değişkenlere Başvurma Desteklenmez](#RefNonScalarClosures)  
  
- [SQL Server 2000 ile İç Içe Sorgular Başarısız Olabilir](#NestedQueriesSQL2000)  
  
- [Anonim Türe Yansıtma](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>
## <a name="linq-queries-that-cannot-be-cached"></a>Önbelleğe Alınamayan LINQ Sorguları  
 .NET Framework 4.5 ile başlayarak, LinQ to Ntities sorguları otomatik olarak önbelleğe alınır. Ancak, `Enumerable.Contains` işleci bellek içi koleksiyonlara uygulayan Varlıklara LINQ sorguları otomatik olarak önbelleğe alınmaz. Ayrıca derlenmiş LINQ sorgularında bellek içi koleksiyonları parametrelendirmeye izin verilmez.  
  
<a name="OrderingInfoLost"></a>
## <a name="ordering-information-lost"></a>Kayıp Bilgileri Sıralama  
 Sütunları anonim bir türe yansıtmak, SQL Server 2005 veritabanına karşı "80" uyumluluk düzeyine ayarlanan bazı sorgularda sipariş bilgilerinin kaybolmasına neden olur.  Bu, sipariş eki listesindeki bir sütun adı, aşağıdaki örnekte gösterildiği gibi seçicideki bir sütun adıyla eşleştiğinde oluşur:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>
## <a name="unsigned-integers-not-supported"></a>İmzasız Tümsatörler Desteklenmiyor  
 Varlık Çerçevesi imzasız tamsayıları desteklemediği için, LINQ'dan Varlıklara sorgusunda imzasız bir tamsayı türü belirtilmesi desteklenmez. İmzasız bir karşıcı belirtirseniz, <xref:System.ArgumentException> aşağıdaki örnekte gösterildiği gibi sorgu ifadesi çevirisi sırasında bir özel durum atılır. Bu örnek, ID 48000 olan bir siparişi sorgular.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>
## <a name="type-conversion-errors"></a>Dönüşüm Hatalarını Yazın  
 Visual Basic'te, bir özellik işlevi kullanarak 1 değeri olan SQL Server bit `CByte` türündeki <xref:System.Data.SqlClient.SqlException> bir sütuna eşlendiğinde, "Aritmetik taşaşma hatası" iletisi ile bir a atılır. Aşağıdaki örnek, AdventureWorks örnek veritabanındaki `Product.MakeFlag` sütunu sorgular ve sorgu sonuçları üzerinde tekrarlandığında bir özel durum atılır.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>
## <a name="referencing-non-scalar-variables-not-supported"></a>Skaler Olmayan Değişkenlere Başvurma Desteklenmez  
 Bir sorguda varlık gibi skaler olmayan değişkenlere başvuru önerilmez. Böyle bir sorgu yürütüldüğünde, <xref:System.NotSupportedException> "Türünün `EntityType`sabit bir değeri oluşturamaz. Bu bağlamda yalnızca ilkel türler ('Int32, String ve Guid' gibi) desteklenir."  
  
> [!NOTE]
> Skaler değişkenler koleksiyonuna başvuru desteklenir.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>SQL Server 2000 ile İç Içe Sorgular Başarısız Olabilir  
 SQL Server 2000 ile LINQ to Ntities sorguları, üç veya daha fazla düzey derinliğinde iç içe geçirilmiş Transact-SQL sorguları üretirlerse başarısız olabilir.  
  
<a name="ProjectToAnonymousType"></a>
## <a name="projecting-to-an-anonymous-type"></a>Anonim Türe Yansıtma  
 İlk sorgu yolunuzu, yöntemüzerinde yöntem kullanarak <xref:System.Data.Objects.ObjectQuery%601.Include%2A> ilgili nesneleri <xref:System.Data.Objects.ObjectQuery%601> içerecek şekilde tanımlar ve döndürülen nesneleri anonim bir türe yansıtmak için LINQ'yu kullanırsanız, dahil etme yönteminde belirtilen nesneler sorgu sonuçlarına dahil edilmez.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 İlgili nesneleri almak için döndürülen türleri anonim bir türe yansıtmayın.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - Varlıklar](linq-to-entities.md)
