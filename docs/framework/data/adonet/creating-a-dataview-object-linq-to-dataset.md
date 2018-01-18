---
title: "DataView nesnesi (LINQ-DataSet) oluşturma"
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
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 895f692bc07e8e48904e0829e322788f2aa45337
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>DataView nesnesi (LINQ-DataSet) oluşturma
Oluşturmanın iki yolu vardır bir <xref:System.Data.DataView> içinde [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bağlamı. Oluşturabileceğiniz bir <xref:System.Data.DataView> gelen bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] üzerinden sorgu bir <xref:System.Data.DataTable>, veya bir yazılı veya türsüz oluşturabilirsiniz <xref:System.Data.DataTable>. Her iki durumda da, oluşturduğunuz <xref:System.Data.DataView> birini kullanarak <xref:System.Data.DataTableExtensions.AsDataView%2A> genişletme yöntemleri; <xref:System.Data.DataView> doğrudan oluşturulabilir değil [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] bağlamı.  
  
 Sonra <xref:System.Data.DataView> bırakıldı oluşturulmuş bir Windows forms uygulaması veya ASP.NET uygulaması UI denetimi bağlamak veya için filtreleme ve sıralama ayarlarını değiştirin.  
  
 <xref:System.Data.DataView>Filtreleme ve sıralama gibi dizin kullanabilirsiniz işlemlerinin performansını önemli ölçüde artıran bir dizin oluşturur. Dizini bir <xref:System.Data.DataView> hem olduğunda yerleşik <xref:System.Data.DataView> oluşturulur ve sıralama veya filtreleme herhangi birinde bilgi değiştirilir. Oluşturma bir <xref:System.Data.DataView> ve en az iki kez oluşturulacak dizin sıralama ayarlama veya bilgileri daha sonra filtreleme neden olur: sonra zaman <xref:System.Data.DataView> oluşturulduğu ve yeniden sıralama veya filtre özelliklerden herhangi biri değiştirildiği.  
  
 Sıralama ve filtreleme hakkında daha fazla bilgi için <xref:System.Data.DataView>, bkz: [DataView ile filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) ve [DataView ile sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>DataView bir LINQ veri kümesi sorgu oluşturma  
 A <xref:System.Data.DataView> nesne sonuçlarından oluşturulabilir bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu sonuçları, bir yansıtma nerede, <xref:System.Data.DataRow> nesneleri. Yeni oluşturulan <xref:System.Data.DataView> oluşturulan gelen sorgu bilgileri sıralama ve filtreleme devralır.  
  
> [!NOTE]
>  Çoğu durumda, filtreleme ve sıralama için kullanılan ifadeleri yan etkileri olmamalıdır ve belirleyici olması gerekir. Ayrıca, ifadeleri herhangi içermemelidir sıralama ve filtreleme operations olabileceğinden yürütmeleri, kümesi sayısına bağlı mantığı yürütülen tüm sayısı.  
  
 Oluşturma bir <xref:System.Data.DataView> anonim türleri döndüren bir sorgu veya birleştirme işlemleri gerçekleştirme sorguları desteklenmiyor.  
  
 Yalnızca aşağıdaki sorgu işleçleri oluşturmak için kullanılan bir sorguda desteklenen <xref:System.Data.DataView>:  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Unutmayın bir <xref:System.Data.DataView> oluşturulur bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> yöntemi sorguda adlı son yöntemi olması gerekir. Bu oluşturur aşağıdaki örnekte gösterilen bir <xref:System.Data.DataView> çevrimiçi sipariş toplam son bulma tarihine göre sıralanır:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Dize tabanlı de kullanabilirsiniz <xref:System.Data.DataView.RowFilter%2A> ve <xref:System.Data.DataView.Sort%2A> özellikleri filtrelemek ve sıralamak için bir <xref:System.Data.DataView> sorgudan oluşturulduktan sonra. Bu sıralama temizleyecek ve sorgudan devralınan filtre bilgilerini not edin. Aşağıdaki örnekte bir <xref:System.Data.DataView> gelen bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ile başlayan adların tarafından filtreler sorgu 'S'. Dize tabanlı <xref:System.Data.DataView.Sort%2A> özelliği ayarlanmış sırasını ve adlarını azalan düzende artan soyadları sıralamak için:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>DataView DataTable nesnesinden oluşturma  
 Öğesinden oluşturulan yanı sıra bir [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu, bir <xref:System.Data.DataView> nesnesi, gelen oluşturulabilir bir <xref:System.Data.DataTable> kullanarak <xref:System.Data.DataTableExtensions.AsDataView%2A> yöntemi.  
  
 Aşağıdaki örnekte bir <xref:System.Data.DataView> satış siparişi ayrıntısını tablo ve veri kaynağı olarak ayarlayan bir <xref:System.Windows.Forms.BindingSource> nesnesi. Bu nesne için bir proxy görevi gören bir <xref:System.Windows.Forms.DataGridView> denetim.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Üzerinde filtreleme ve sıralama ayarlanabilir <xref:System.Data.DataView> gelen oluşturulduktan sonra bir <xref:System.Data.DataTable>. Aşağıdaki örnekte bir <xref:System.Data.DataView> başvurun ve ayarlar <xref:System.Data.DataView.Sort%2A> özelliği sırasını ve adlarını azalan düzende artan soyadları sıralamak için:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Ancak, ayarı ile birlikte gelen bir performans kaybı yoktur <xref:System.Data.DataView.RowFilter%2A> veya <xref:System.Data.DataView.Sort%2A> sonra özelliği <xref:System.Data.DataView> bir sorgudan oluşturuldu <xref:System.Data.DataView> filtreleme ve sıralama işlemleri desteklemek için bir dizin oluşturur. Ayarı <xref:System.Data.DataView.RowFilter%2A> veya <xref:System.Data.DataView.Sort%2A> özelliği veri yükü uygulamanıza ekleme ve performans azaltmak için dizini yeniden oluşturur. Mümkün olduğunda, ilk oluşturduğunuzda bilgi sıralama ve filtreleme belirtmek daha iyi <xref:System.Data.DataView> ve daha sonra değiştirme kaçının.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Bağlama ve LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [DataView ile Filtreleme](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [DataView ile Sıralama](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
