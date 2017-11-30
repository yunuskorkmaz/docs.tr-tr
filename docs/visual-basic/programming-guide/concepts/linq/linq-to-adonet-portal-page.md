---
title: "ADO.NET'e LINQ (Portal Sayfası)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b5cbbca716cc7de36541aecd630eb9a98815f5a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-adonet-portal-page"></a>ADO.NET'e LINQ (Portal Sayfası)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)]herhangi bir numaralandırılabilir nesnesinde üzerinden sorgu sağlar [!INCLUDE[vstecado](~/includes/vstecado-md.md)] kullanarak [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] programlama modeli.  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] Belgeleri, .NET Framework SDK ADO.NET bölümünde bulunur: [LINQ ve ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).  
  
 Üç ayrı ADO.NET vardır [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] teknolojileri: [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], ve [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]daha zengin, en iyi duruma getirilmiş üzerinden sorgulama sağlar <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] doğrudan sorgu olanak tanır [!INCLUDE[ssNoVersion](~/includes/ssnoversion-md.md)] veritabanı şemalarını ve [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] sorgu sayesinde bir [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 <xref:System.Data.DataSet> En yaygın olarak kullanılan bileşenlerinde biri [!INCLUDE[vstecado](~/includes/vstecado-md.md)], ve olan bağlantısı kesilmiş programlama anahtar öğesi modeli [!INCLUDE[vstecado](~/includes/vstecado-md.md)] üzerine kurulmuştur. Bu teklifleriyle, ancak rağmen <xref:System.Data.DataSet> sorgu yeteneği sınırlıdır.  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]daha zengin sorgu özelliklerini oluşturmanıza olanak sağlayan <xref:System.Data.DataSet> diğer birçok veri kaynakları için kullanılabilir aynı sorgu işlevini kullanarak.  
  
 Daha fazla bilgi için bkz: [LINQ-DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]İlişkisel veri nesneleri olarak yönetmek için bir çalışma zamanı altyapısı sağlar. İçinde [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], ilişkisel veritabanı veri modelinin Geliştirici programlama dilinde ifade nesne modeli eşlenir. Uygulama yürüttüğünüzde [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL'e dil ile tümleşik sorgu nesne modelinde dönüşür ve yürütme için veritabanı gönderir. Veritabanı sonuçları döndürdüğünde [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] geri yönetebilirsiniz nesnelerine çevirir.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]nesne modelinde devralma ve saklı yordamları ve veritabanındaki kullanıcı tanımlı işlevler için destek içerir.  
  
 Daha fazla bilgi için bkz: [LINQ-SQL](https://msdn.microsoft.com/library/bb386976).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  
 Aracılığıyla [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)], ilişkisel veri .NET ortamı nesneler olarak gösterilir. Bu katman için ideal bir hedef nesnesi haline getirir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] desteği, iş mantığı oluşturmak için kullanılan dil veritabanından sorguları formüle yayınlamasına izin verme. Bu özellik olarak bilinen [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. Bkz: [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) daha fazla bilgi için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ ve ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)  
 [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
