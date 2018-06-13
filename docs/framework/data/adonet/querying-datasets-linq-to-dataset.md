---
title: Veri kümeleri (LINQ-DataSet) sorgulama
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 18daed2ee4196a03af818dfbd0e65153ae43a840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361766"
---
# <a name="querying-datasets-linq-to-dataset"></a>Veri kümeleri (LINQ-DataSet) sorgulama
Sonra bir <xref:System.Data.DataSet> nesnesi, verilerle doldurulur, bu sorgulama başlayabilirsiniz. Sorgularıyla formulating [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanmaya benzer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] diğer karşı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-veri kaynaklarının etkin. Kullandığınızda, ancak unutmayın [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] üzerinden sorgular bir <xref:System.Data.DataSet> numaralandırması sorgulama nesne <xref:System.Data.DataRow> nesneleri yerine bir özel tür numaralandırması. Bu tüm üyeleri kullanabileceğiniz anlamına gelir <xref:System.Data.DataRow> sınıfını, [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgular. Bu, zengin, karmaşık sorgular oluşturmanıza olanak sağlar.  
  
 Diğer uygulamaları ile [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], oluşturabileceğiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] iki farklı form sorgularda: Sorgu ifade sözdizimi ve yöntem temelli sorgu sözdizimi. İki yöntemden birini hakkında daha fazla bilgi için bkz: [LINQ ile çalışmaya başlama](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Sorgu ifade sözdizimi kullanabilir veya gerçekleştirmek için yöntem temelli sorgu söz dizimi sorgular tek tablolarda karşı bir <xref:System.Data.DataSet>, birden fazla tabloya karşı bir <xref:System.Data.DataSet>, veya bir yazılı tablolarda karşı <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Tek Tablolu Sorgular](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Tek tablo sorguları gerçekleştirmeyi açıklar.  
  
 [Tablolar Arası Sorgular](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Geçici tablo sorguları gerçekleştirmeyi açıklar.  
  
 [Türü Belirtilmiş DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Sorgu açıklar yazılan <xref:System.Data.DataSet> nesneleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [DataSet’e Veri Yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
