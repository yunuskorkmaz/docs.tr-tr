---
title: LINQ - DataSet
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3746fb31c66202dc75c6aff3ce69952f25b06931
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="linq-to-dataset"></a>LINQ - DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] daha kolay ve hızlı sorguya, önbelleğe alınan veriler üzerinde kolaylaştırır bir <xref:System.Data.DataSet> nesnesi. Özellikle, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorguları programlama dili kendisi yerine ayrı sorgu dilini kullanarak yazmak geliştiricilere etkinleştirerek sorgulama basitleştirir. Bu artık, derleme zamanı sözdizimi denetimi, statik yazarak ve IntelliSense desteği sorgularını Visual Studio tarafından sağlanan yararlanabilir Visual Studio geliştiriciler için özellikle yararlıdır.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Ayrıca kullanılabilir bir veya daha fazla veri kaynaklarından birleştirilmiş veriler üzerinde sorgulanamıyor. Bu verilerin temsil ve işlenmiş, yerel olarak toplanan verileri ve orta katman Web uygulamalarında önbelleğe alma sorgulama gibi esneklik gerektiren birçok senaryolara olanak sağlar. Özellikle, genel raporlama, analiz ve business Intelligence uygulamalar bu yöntem işlemlerinde gerektirir.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] İşlevselliği genişletme yöntemleri aracılığıyla gösterilir <xref:System.Data.DataRowExtensions> ve <xref:System.Data.DataTableExtensions> sınıfları. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] üzerine kurulur ve varolan kullanır [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] mimarisi ve değiştirmek için tasarlanmamıştır [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] uygulama kodundaki. Varolan ADO.NET 2.0 kod içinde çalışmaya devam edecek bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] uygulama. İlişki [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] için [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] ve veri depolama alanı aşağıdaki çizimde gösterilmiştir.  
  
 ![LINQ-DataSet ADO.NET sağlayıcısını temel](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ ve ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)
