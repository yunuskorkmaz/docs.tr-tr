---
title: "Veri kümeleri (LINQ-DataSet) sorgulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4f1b1a70025dc81bdf99c636b65c23d373e73a80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="querying-datasets-linq-to-dataset"></a>Veri kümeleri (LINQ-DataSet) sorgulama
Sonra bir <xref:System.Data.DataSet> nesnesi, verilerle doldurulur, bu sorgulama başlayabilirsiniz. Sorgularıyla formulating [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanmaya benzer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] diğer karşı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-veri kaynaklarının etkin. Kullandığınızda, ancak unutmayın [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] üzerinden sorgular bir <xref:System.Data.DataSet> numaralandırması sorgulama nesne <xref:System.Data.DataRow> nesneleri yerine bir özel tür numaralandırması. Bu tüm üyeleri kullanabileceğiniz anlamına gelir <xref:System.Data.DataRow> sınıfını, [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorgular. Bu, zengin, karmaşık sorgular oluşturmanıza olanak sağlar.  
  
 Diğer uygulamaları ile [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], oluşturabileceğiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] iki farklı form sorgularda: Sorgu ifade sözdizimi ve yöntem temelli sorgu sözdizimi. İki yöntemden birini hakkında daha fazla bilgi için bkz: [LINQ ile çalışmaya başlama](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Sorgu ifade sözdizimi kullanabilir veya gerçekleştirmek için yöntem temelli sorgu söz dizimi sorgular tek tablolarda karşı bir <xref:System.Data.DataSet>, birden fazla tabloya karşı bir <xref:System.Data.DataSet>, veya bir yazılı tablolarda karşı <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Tek tablolu sorgular](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Tek tablo sorguları gerçekleştirmeyi açıklar.  
  
 [Geçici tablo sorguları](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Geçici tablo sorguları gerçekleştirmeyi açıklar.  
  
 [Yazılan veri kümeleri sorgulama](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Sorgu açıklar yazılan <xref:System.Data.DataSet> nesneleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-DataSet örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Bir veri kümesine veri yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
