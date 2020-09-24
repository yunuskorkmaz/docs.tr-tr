---
title: LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 0d36461cea68383e070db80d85f596151bd9c2ae
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161964"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler

Bu bölüm LINQ to Entities sorgularıyla ilgili bilinen sorunlar hakkında bilgi sağlar.  
  
- [Önbelleğe alınabilecek LINQ sorguları](#LINQQueriesThatAreNotCached)  
  
- [Sipariş bilgileri kayıp](#OrderingInfoLost)  
  
- [İşaretsiz tamsayılar desteklenmiyor](#UnsignedIntsUnsupported)  
  
- [Tür dönüştürme hataları](#TypeConversionErrors)  
  
- [Skalar olmayan değişkenlere başvurma desteklenmiyor](#RefNonScalarClosures)  
  
- [İç içe geçmiş sorgular SQL Server 2000 ile başarısız olabilir](#NestedQueriesSQL2000)  
  
- [Anonim bir türe yansıtma](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>

## <a name="linq-queries-that-cannot-be-cached"></a>Önbelleğe alınabilecek LINQ sorguları  

 .NET Framework 4,5 ' den başlayarak LINQ to Entities sorguları otomatik olarak önbelleğe alınır. Ancak, bu `Enumerable.Contains` işleci, bellek içi koleksiyonlara uygulayan LINQ to Entities sorguları otomatik olarak önbelleğe alınmaz. Ayrıca, derlenen LINQ sorgularında bellek içi koleksiyonlara parametreleştirmeye izin verilmez.  
  
<a name="OrderingInfoLost"></a>

## <a name="ordering-information-lost"></a>Sipariş bilgileri kayıp  

 Sütunları anonim bir türde yansıtma, bir SQL Server 2005 veritabanına karşı yürütülen bazı sorgularda sıralama bilgilerinin "80" uyumluluk düzeyine ayarlanmış olarak kaybolmasına neden olur.  Bu durum, aşağıdaki örnekte gösterildiği gibi, order by listesindeki bir sütun adı seçicideki bir sütun adıyla eşleştiğinde meydana gelir:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>

## <a name="unsigned-integers-not-supported"></a>İşaretsiz tamsayılar desteklenmiyor  

 Entity Framework işaretsiz tamsayılar desteklemediğinden LINQ to Entities sorgusunda işaretsiz bir tamsayı türü belirtilmesi desteklenmez. İşaretsiz bir tamsayı belirtirseniz, <xref:System.ArgumentException> Aşağıdaki örnekte gösterildiği gibi sorgu ifadesi çevirisi sırasında bir özel durum atılır. Bu örnek 48000 KIMLIKLI bir sipariş için sorgular.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>

## <a name="type-conversion-errors"></a>Tür dönüştürme hataları  

 Visual Basic, bir özellik işlevi kullanılarak 1 değeri olan SQL Server bit türünde bir sütunla eşlendiğinde `CByte` , bir <xref:System.Data.SqlClient.SqlException> "aritmetik taşma hatası" iletisiyle oluşturulur. Aşağıdaki örnek, `Product.MakeFlag` AdventureWorks örnek veritabanındaki sütununu sorgular ve sorgu sonuçları üzerinden yineedildiğinde bir özel durum oluşturulur.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>

## <a name="referencing-non-scalar-variables-not-supported"></a>Skalar olmayan değişkenlere başvurma desteklenmiyor  

 Bir sorgu içindeki bir varlık gibi skaler olmayan değişkenlere başvurma desteklenmez. Böyle bir sorgu yürütüldüğünde, <xref:System.NotSupportedException> "türün sabit değeri oluşturulamıyor" iletisini içeren bir özel durum oluşturulur `EntityType` . Bu bağlamda yalnızca ilkel türler (Int32, String ve Guid gibi) destekleniyor. "  
  
> [!NOTE]
> Skaler değişkenler koleksiyonuna başvurmak desteklenir.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>

## <a name="nested-queries-may-fail-with-sql-server-2000"></a>İç içe geçmiş sorgular SQL Server 2000 ile başarısız olabilir  

 SQL Server 2000 ile, üç veya daha fazla düzey derinlikli iç içe Transact-SQL sorguları oluşturduklarında LINQ to Entities sorguları başarısız olabilir.  
  
<a name="ProjectToAnonymousType"></a>

## <a name="projecting-to-an-anonymous-type"></a>Anonim bir türe yansıtma  

 Üzerinde yöntemi kullanarak ilgili nesneleri dahil etmek için ilk sorgu yolunu tanımlayabilir <xref:System.Data.Objects.ObjectQuery%601.Include%2A> <xref:System.Data.Objects.ObjectQuery%601> ve ardından döndürülen nesneleri anonim bir türe eklemek için LINQ kullandığınızda, Include yönteminde belirtilen nesneler sorgu sonuçlarına dahil edilmez.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 İlgili nesneleri almak için, döndürülen türleri bir anonim türe proje olarak değiştirmeyin.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - Varlıklar](linq-to-entities.md)
