---
title: LINQ - DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: d7ebf32467c7ed1d54279a93c5052e7a52dc52f7
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462727"
---
# <a name="linq-to-dataset"></a>LINQ - DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] daha kolay ve hızlı sorgu için verileri önbelleğe üzerinde kolaylaştırır bir <xref:System.Data.DataSet> nesne. Özellikle, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorguları programlama dilinden kendisi yerine ayrı bir sorgu dilini kullanarak yazma geliştiricilerin etkinleştirerek sorgulama basitleştirir. Bu, özellikle artık derleme zamanı söz dizimi denetimini statik yazmaya ve sorguları Visual Studio tarafından sağlanan IntelliSense desteği yararlanabilirsiniz Visual Studio geliştiriciler için yararlıdır.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Ayrıca bir veya daha fazla veri kaynağından birleştirilmiş veriler üzerinde sorgu için. Bu, yerel olarak toplanan verileri ve orta katman Web uygulamalarında önbelleğe alma sorgulama gibi işlenen verilerin nasıl temsil ve esneklik gerektiren birçok senaryolarını olanaklı kılar. Özellikle, bu yöntem işlemlerinde genel raporlama, analiz ve iş zekası uygulamaları gerektirir.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] İşlevi sunulmuştur alanında uzantı yöntemlerini yoluyla <xref:System.Data.DataRowExtensions> ve <xref:System.Data.DataTableExtensions> sınıfları. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] temel alır ve mevcut kullanan [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] mimari ve değiştirmek için tasarlanmamıştır [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] uygulama kodunda. Var olan ADO.NET 2.0 kod içinde çalışmaya devam edecek bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] uygulama. İlişkiyi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] için [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] ve veri deposu Aşağıdaki diyagramda gösterilmiştir.  
  
 ![LINQ to DataSet ADO.NET sağlayıcısını dayalı olduğunu gösteren diyagram.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Başlarken](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Dil ile tümleşik sorgu (LINQ)-C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Dil ile tümleşik sorgu (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ ve ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
