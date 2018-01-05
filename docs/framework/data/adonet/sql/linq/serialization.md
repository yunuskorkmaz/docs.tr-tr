---
title: Serialization2
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
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 60f73644a047230a590e75f095575cf85140f3a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="serialization"></a>Serileştirme
Bu konuda açıklanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] seri hale getirme özellikleri. İzleyin paragrafları tasarım zamanı ve çalışma zamanı serileştirme davranışını serileştirme kod oluşturma sırasında ekleme hakkında bilgi sağlayan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sınıfları.  
  
 Seri hale getirme kod aşağıdaki yöntemlerden birini bir tasarım zamanında ekleyebilirsiniz:  
  
-   İçinde [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], değiştirme **seri hale getirme modu** özelliğine **Unidirectional**.  
  
-   SQLMetal komut satırında ekleme **/serialization** seçeneği. Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  
 Tarafından oluşturulan kodu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varsayılan olarak ertelenmiş yükleme özellikleri sağlar. Ertelenen yükleme Orta katmanda çok istek üzerine veri saydam yüklenmesi için uygundur. Ancak, ertelenmiş yükleme veya istenip istenmediğini ertelenmiş yüklenirken seri hale getirici tetikler olduğundan seri hale getirme için sorunlu oluşturur. Bir nesne seri, uygulamada kendi geçişli kapatma erteleneceği yüklenen tüm giden başvuruları altında serileştirilir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Serileştirme özelliği temelde iki mekanizma bu sorunu giderir:  
  
-   A <xref:System.Data.Linq.DataContext> yüklenirken ertelenmiş kapatma modu (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>). Daha fazla bilgi için bkz. <xref:System.Data.Linq.DataContext>.  
  
-   Oluşturmak için bir kod oluşturma anahtar <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> ve <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> oluşturulan varlıkları öznitelikleri. Seri hale getirme, altındaki erteleneceği yükleme sınıfların davranışını dahil olmak üzere bu yönünün önemli konu, bu konunun ' dir.  
  
### <a name="definitions"></a>Tanımlar  
  
-   *DataContract seri hale getirici*: varsayılan .NET Framework 3.0 veya sonraki sürümleri, Windows Communication Framework (WCF) bileşeni tarafından kullanılan serileştirici.  
  
-   *Tek yönlü serileştirme*: (bir döngü önlemek için) yalnızca bir tek yönlü ilişkilendirme özelliği içeren bir sınıf serileştirilmiş sürümü. Kurala göre birincil yabancı anahtar ilişkisi üst tarafındaki özelliği seri hale getirme için işaretlenmiş. Çift yönlü bir ilişkilendirmeye diğer taraftaki serileştirilmemiş.  
  
     Tek yönlü serileştirme türüdür yalnızca tarafından desteklenen serileştirme [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="code-example"></a>Kod Örneği  
 Aşağıdaki kod geleneksel kullanır `Customer` ve `Order` sınıfları Northwind örnek veritabanından ve bu sınıfların serileştirme özniteliklerle nasıl donatılmış gösterir.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 İçin `Order` aşağıdaki örnekte, yalnızca karşılık gelen ters ilişkilendirme özelliği sınıfı `Customer` sınıfı okumanızdır gösterilir. Sahip olmayan bir `DataMember` bir döngü önlemek için öznitelik.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Varlıkları seri hale getirmek nasıl  
 Önceki bölümde aşağıda gösterilen kodları varlıklarda seri hale getirebilir;  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Kendi kendine özyinelemeli ilişkileri  
 Kendi kendine özyinelemeli ilişkileri aynı düzeni uygular. Yabancı anahtar karşılık gelen association özelliğine sahip olmayan bir `DataMember` üst özelliği yapar ancak özniteliği.  
  
 İki self özyinelemeli ilişkisi olan aşağıdaki sınıfı göz önünde bulundurun: Employee.Manager/Reports ve Employee.Mentor/Mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [SqlMetal.exe (Kod Üretme Aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)
