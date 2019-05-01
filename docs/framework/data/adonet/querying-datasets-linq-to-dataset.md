---
title: (LINQ to DataSet) DataSet'leri sorgulama
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: a1c316811ce08141999bcec4c9c8504f86c2e285
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878689"
---
# <a name="querying-datasets-linq-to-dataset"></a>(LINQ to DataSet) DataSet'leri sorgulama
Sonra bir <xref:System.Data.DataSet> nesne verilerle doldurulduğunda, sorgulama başlayabilirsiniz. Sorgularla formulating [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanmaya benzer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] diğer karşı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-veri kaynakları etkin. Kullandığınızda, ancak unutmayın [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] üzerinden sorgular bir <xref:System.Data.DataSet> numaralandırması sorguladığınız nesne <xref:System.Data.DataRow> nesneler yerine özel bir tür numaralandırması. Bu tüm üyelerinin kullanabileceği anlamına gelir <xref:System.Data.DataRow> sınıfını, [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgular. Bu, zengin, karmaşık sorgular oluşturmanıza olanak sağlar.  
  
 Diğer uygulamaları ile [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], oluşturabileceğiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] iki farklı form sorgularda: sorgu ifadesi söz dizimi ve metot tabanlı sorgu söz dizimi. Sorgu ifadesi söz dizimi kullanabilir veya tek bir tabloda sorguları gerçekleştirmek için metot tabanlı sorgu söz dizimi bir <xref:System.Data.DataSet>, birden çok tablodan karşı bir <xref:System.Data.DataSet>, veya bir türü belirtilmiş tablolarında karşı <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Tek Tablolu Sorgular](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Tek tablo sorguları gerçekleştirmeyi açıklar.  
  
 [Tablolar Arası Sorgular](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Tablolar arası sorgular yerine getirilmesi anlatılmaktadır.  
  
 [Türü Belirtilmiş DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Sorgu açıklar yazılan <xref:System.Data.DataSet> nesneleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [DataSet’e Veri Yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
