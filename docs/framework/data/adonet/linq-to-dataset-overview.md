---
title: LINQ-DataSet genel bakış
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: d269ea2899ffd8005aad9912cf9273a012e13edd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765626"
---
# <a name="linq-to-dataset-overview"></a>LINQ-DataSet genel bakış
<xref:System.Data.DataSet> Daha yaygın olarak kullanılan bileşenlerden biri [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Anahtar öğesi bağlantısı kesilmiş olan programlama modeli [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] , temel alır ve bunu, farklı veri kaynaklarından açıkça Önbellek verileri olanak tanır. Sunu katmanı için <xref:System.Data.DataSet> veri bağlama için GUI denetimleri ile tümleşiktir. Orta katman için veri ilişkisel şeklini korur ve hızlı Basit Sorgu ve hiyerarşi Gezinti hizmetleri içeren bir önbellek sağlar. Bir veritabanı isteklerinde sayısını azaltmak için kullanılan ortak kullanmak için bir tekniktir <xref:System.Data.DataSet> orta katman önbelleğe alma için. Örneğin, veri güdümlü göz önünde bulundurun [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web uygulaması. Genellikle, uygulama verilerini önemli bir kısmını sık değişmeyen ve oturumlar veya kullanıcılar arasında ortak olan. Bu veriler veritabanında istek sayısını azaltan ve kullanıcının etkileşimleri hızlandırır Web sunucusu üzerindeki bellekte tutulabilir. Başka bir yararlı yönünü <xref:System.Data.DataSet> veri alt kümesi uygulama alanına bir veya daha fazla veri kaynağından getirmek bir uygulama tanımasıdır. Uygulama, ilişkisel şeklini koruyarak veri bellek içi, ardından yönetebilirsiniz.  
  
 Kendi teklifleriyle rağmen <xref:System.Data.DataSet> sorgu yeteneği sınırlıdır. <xref:System.Data.DataTable.Select%2A> Yöntemi, filtreleme ve sıralama, için kullanılabilir ve <xref:System.Data.DataRow.GetChildRows%2A> ve <xref:System.Data.DataRow.GetParentRow%2A> metotları hiyerarşi gezinti için kullanılabilir. Herhangi bir şey için daha karmaşık, ancak, geliştiricinin özel bir sorgu yazmanız gerekir. Bu, kötü gerçekleştirmek ve korumak zor olan uygulamalarda neden olabilir.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] daha kolay ve hızlı sorguya, önbelleğe alınan veriler üzerinde kolaylaştırır bir <xref:System.Data.DataSet> nesnesi. Bu sorguları programlama dilinde kendisini belirtilmiştir yerine uygulama kodunda katıştırılmış değişmez değerleri dize. Başka bir deyişle, geliştiricilerin ayrı bir sorgu dili öğrenmeniz gerekmez. Ayrıca, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Visual Studio IDE derleme zamanı sözdizimi denetimi, statik yazarak ve için IntelliSense desteği sağladığından daha verimli çalışmak Visual Studio geliştiricilerinin [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Ayrıca kullanılabilir bir veya daha fazla veri kaynaklarından birleştirilmiş veriler üzerinde sorgulanamıyor. Bu verinin nasıl temsil ve işlenmiş esneklik gerektiren birçok senaryolara olanak sağlar. Özellikle, genel raporlama, analiz ve business Intelligence uygulamalar bu yöntem işlemlerinde gerektirir.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>LINQ-DataSet kullanan veri Setleri sorgulama  
 Sorgulama başlamadan önce bir <xref:System.Data.DataSet> kullanarak nesne [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], doldurmanız gerekir <xref:System.Data.DataSet>. Verileri yüklemek için birkaç yol vardır bir <xref:System.Data.DataSet>, örneğin kullanarak <xref:System.Data.Common.DataAdapter> sınıfı veya [LINQ-SQL](../../../../docs/framework/data/adonet/sql/linq/index.md). Verilerin içine yüklendikten sonra bir <xref:System.Data.DataSet> nesnesi, bu sorgu başlayabilir. Formulating kullanarak sorguları [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kullanmaya benzer [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] diğer karşı [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-veri kaynaklarının etkin. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorguları, tek tablolarda karşı yapılabilir bir <xref:System.Data.DataSet> veya kullanarak birden fazla tablo karşı <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> standart sorgu işleçleri.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] sorguları karşı yazılan hem hem de türsüz desteklenir <xref:System.Data.DataSet> nesneleri. Varsa şeması <xref:System.Data.DataSet> uygulama tasarım zamanında yazılmış bir bilinen <xref:System.Data.DataSet> önerilir. İçinde yazılmış bir <xref:System.Data.DataSet>, tablolar ve satır sorguları daha basit ve daha okunabilir hale getirir sütunların her biri için olarak belirtilmiş üyeler olmalıdır.  
  
 Standart sorgu işleçleri System.Core.dll içinde uygulanan yanı sıra [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] birkaç ekler <xref:System.Data.DataSet>-sorgu üzerinde bir dizi kolaylaştırmak için belirli uzantılara <xref:System.Data.DataRow> nesneleri. Bunlar <xref:System.Data.DataSet>-belirli uzantılara sütun değerlerini erişim sağlayan yöntemler yanı sıra satır dizilerini Karşılaştırma işleçleri dahil bir <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N katmanlı uygulamalar ve LINQ-DataSet  
 N katmanlı veri uygulamalarını birden çok mantıksal katman (veya katmanları) ayrılmış veri merkezli uygulamalardır. Tipik bir N katmanlı uygulama sunu katmanı, orta katman ve veri katmanı içerir. Uygulama bileşenleri ayrı katmanlara ayırma Bakım ve uygulama ölçeklenebilirliği artırır. N katmanlı veri uygulamaları hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).  
  
 N katmanlı uygulamalarda <xref:System.Data.DataSet> genellikle önbellek bilgilere orta katman bir Web uygulaması için kullanılır. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] İşlevselliği sorgulama genişletme yöntemleri uygulanır ve mevcut ADO.NET 2.0 genişletir <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
