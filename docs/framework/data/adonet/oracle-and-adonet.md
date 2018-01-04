---
title: Oracle ve ADO.NET
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
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f77d5c98c96bd4b6085c30b6d1dd713bd324fbad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-and-adonet"></a>Oracle ve ADO.NET
> [!NOTE]
>  Türler <xref:System.Data.OracleClient> kullanım dışı bırakılmıştır. Türleri geçerli sürüm of.NET Framework içinde desteklenen kalır, ancak gelecekteki bir sürümde kaldırılacak. Microsoft, üçüncü taraf Oracle sağlayıcısı kullanmanızı önerir.  
  
 Bu bölümde özellikleri ve özgü davranışları açıklanmaktadır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için Oracle veri sağlayıcısı.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcısı Oracle için Oracle Çağrı Arabirimi (OCI) Oracle istemci yazılımı tarafından sağlanan adımları kullanarak bir Oracle veritabanına erişim sağlar. Veri sağlayıcısı işlevselliğini benzer şekilde tasarlanmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için veri sağlayıcıları [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], OLE DB ve ODBC.  
  
 Kullanılacak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için Oracle veri sağlayıcısı, bir uygulama başvurmalıdır <xref:System.Data.OracleClient> şekilde ad alanı:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Kodunuzu derlerken DLL bir başvuru eklemeniz gerekir. Örneğin, C# programı derleme, komut satırında içermelidir:  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sistem Gereksinimleri](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Kullanma gereksinimleri açıklanır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] , Oracle için veri sağlayıcı ve onu kullanırken dikkate etmeniz gereken sorunlar sayısını tanımlar.  
  
 [Oracle BFILE](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 Açıklar <xref:System.Data.OracleClient.OracleBFile> Oracle BDOSYA veri türü ile çalışmak için kullanılan sınıf.  
  
 [Oracle LOB](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 Açıklar <xref:System.Data.OracleClient.OracleLob> Oracle LOB veri türleriyle çalışmak için kullanılan sınıf.  
  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 Oracle REF İMLEÇ veri türü için destek açıklanır.  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 Dahil olmak üzere Oracle veri türleriyle çalışmak için kullanabileceğiniz yapıları açıklar <xref:System.Data.OracleClient.OracleNumber> ve <xref:System.Data.OracleClient.OracleString>.  
  
 [Oracle Dizileri](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 Anahtar Oracle sırası sunucu tarafından üretilen değerleri almak için destek açıklanır.  
  
 [Oracle Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Oracle veri türlerini ve bunların eşlemelere listeler <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Oracle Dağıtılmış İşlemleri](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 Açıklar nasıl <xref:System.Data.OracleClient.OracleConnection> nesne bir işlem etkin olduğunu belirlerse, varolan bir dağıtılmış işlemde otomatik olarak kaydeder.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Güvenli kodlama uygulamalarını kullanırken açıklar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Oluşturma ve kullanma açıklar `DataSets`, yazılı `DataSets`, `DataTables`, ve `DataViews`.  
  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 ADO.NET veri ile nasıl çalışılacağını açıklar.  
  
 [SQL Server ve ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 Özellikleri ve özgü işlevleri ile nasıl çalışılacağını açıklar [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Sağlayıcı bağımsız kod yazmanıza izin Genel sınıflar açıklanmaktadır [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
