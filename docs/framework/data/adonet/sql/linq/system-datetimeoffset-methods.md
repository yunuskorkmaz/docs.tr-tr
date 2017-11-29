---
title: "System.DateTimeOffset yöntemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cbcd2af0b06eeb85c30c8a451877f5913e5d89e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemdatetimeoffset-methods"></a>System.DateTimeOffset yöntemleri
Nesne modeli ya da dış eşleme dosyası eşlenen sonra LINQ-SQL çoğunu çağrı sayesinde <xref:System.DateTimeOffset?displayProperty=nameWithType> yöntemleri, işleçler ve özelliklerinden, LINQ to SQL sorguları.  
  
 Desteklenmeyen yalnızca bu devralınan gelen yöntemlerdir <xref:System.Object?displayProperty=nameWithType> , yapmayın algılama LINQ bağlamında SQL sorguları gibi: `Finalize`, `GetHashCode`, `GetType`, ve `MemberwiseClone`. LINQ-SQL bunları SQL Server üzerine yürütülmek çeviremez çünkü bu yöntemleri desteklenmez.  
  
> [!NOTE]
>  Ortak dil çalışma zamanı (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısı ve bir SQL eşleme özelliğini `DATETIMEOFFSET` LINQ-SQL, sütunla .NET Framework 3.5 SP1 gerektirir veya sonrasını. SQL `DATETIMEOFFSET` sütundur yalnızca Microsoft SQL Server 2008 ve sonrasındaki kullanılabilir.  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods tarih ve saat yöntemleri  
 Tarafından sunulan yöntemleri yanı sıra <xref:System.DateTimeOffset> yapısı, LINQ-SQL, aşağıdaki tabloda listelenen yöntemleri sunar <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> tarih ve saat ile çalışmak için sınıf.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Nesne modeli oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [SQL CLR türü eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
