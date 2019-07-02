---
title: LINQ - DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504358"
---
# <a name="linq-to-dataset"></a>LINQ - DataSet
LINQ to DataSet kolaylaştırır ve veriler üzerinde sorgu için daha hızlı bir şekilde önbelleğe bir <xref:System.Data.DataSet> nesne. Özellikle, LINQ to DataSet sorguları programlama dilinden kendisi yerine ayrı bir sorgu dilini kullanarak yazma geliştiricilerin etkinleştirerek sorgulama basitleştirir. Bu, özellikle artık derleme zamanı söz dizimi denetimini statik yazmaya ve sorguları Visual Studio tarafından sağlanan IntelliSense desteği yararlanabilirsiniz Visual Studio geliştiriciler için yararlıdır.  
  
 LINQ to DataSet de kullanılabilir bir veya daha fazla veri kaynağından birleştirilmiş veriler üzerinde sorgu için. Bu, yerel olarak toplanan verileri ve orta katman Web uygulamalarında önbelleğe alma sorgulama gibi işlenen verilerin nasıl temsil ve esneklik gerektiren birçok senaryolarını olanaklı kılar. Özellikle, bu yöntem işlemlerinde genel raporlama, analiz ve iş zekası uygulamaları gerektirir.  
  
 LINQ to DataSet işlevselliğini alanında uzantı yöntemlerini yoluyla kullanıma sunulan <xref:System.Data.DataRowExtensions> ve <xref:System.Data.DataTableExtensions> sınıfları. LINQ to DataSet temel alır ve mevcut ADO.NET mimarisini kullanır ve uygulama kodunda ADO.NET değiştirmek üzere tasarlanmamıştır. ADO.NET kod mevcut bir LINQ to DataSet uygulama çalışmaya devam eder. LINQ to DataSet ADO.NET ve veri deposu arasındaki ilişki, aşağıdaki diyagramda gösterilmiştir.  
  
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
