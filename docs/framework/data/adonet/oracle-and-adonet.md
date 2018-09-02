---
title: Oracle ve ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 9a60499674f0192bb7589f227bffb6f907f682d9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452586"
---
# <a name="oracle-and-adonet"></a>Oracle ve ADO.NET
> [!NOTE]
>  Türlerinde <xref:System.Data.OracleClient> kullanım dışı bırakılmıştır. Türleri geçerli sürümü of.NET Framework içinde desteklenen kalır, ancak gelecekteki bir sürümde kaldırılacak. Microsoft, üçüncü taraf Oracle sağlayıcısı kullanmanızı önerir.  
  
 Bu bölümde, özellikleri ve özel davranışları açıklanmaktadır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için Oracle veri sağlayıcısı.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin Oracle veri sağlayıcısı, Oracle istemci yazılımı tarafından sağlanan Oracle Çağrı Arabirimi (OCI) kullanarak bir Oracle veritabanına erişim sağlar. Veri sağlayıcısı işlevselliğini benzer olacak şekilde tasarlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server, OLE DB ve ODBC veri sağlayıcıları.  
  
 Kullanılacak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Oracle için veri sağlayıcısı, bir uygulama başvurmalıdır <xref:System.Data.OracleClient> gösterildiği gibi ad alanı:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Kodunuzu derlediğinizde de DLL'ye bir başvuru içermelidir. Örneğin, bir C# programı derleme yapıyorsanız, komut satırınızda içermelidir:  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sistem Gereksinimleri](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Kullanmak için gereksinimleri anlatılmaktadır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için Oracle veri sağlayıcısı ve bir dizi, kullanırken dikkat edilmesi gereken sorunlar açıklanır.  
  
 [Oracle BFILE](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 Açıklar <xref:System.Data.OracleClient.OracleBFile> Oracle BDOSYA veri türü ile çalışmak için kullanılan sınıf.  
  
 [Oracle LOB](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 Açıklar <xref:System.Data.OracleClient.OracleLob> Oracle LOB veri türleriyle çalışmak için kullanılan sınıf.  
  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 Oracle REF CURSOR veri türü için destek açıklanır.  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 Yapıları dahil olmak üzere Oracle veri türleriyle çalışmak için kullanabileceğiniz açıklar <xref:System.Data.OracleClient.OracleNumber> ve <xref:System.Data.OracleClient.OracleString>.  
  
 [Oracle Dizileri](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 Anahtar Oracle sırası sunucu tarafından oluşturulan değerleri almak için destek açıklanır.  
  
 [Oracle Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Oracle veri türleri ve eşleşmeleri listeler <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Oracle Dağıtılmış İşlemleri](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 Açıklayan nasıl <xref:System.Data.OracleClient.OracleConnection> nesne bir işlem etkin olduğunu belirlerse, varolan bir dağıtılmış işlemde otomatik olarak kaydeder.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Güvenli kodlama uygulamalarını kullanırken tanımlar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Oluşturma ve kullanma işlemini açıklamaktadır `DataSets`, belirlenmiş `DataSets`, `DataTables`, ve `DataViews`.  
  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 ADO.NET'te veri ile nasıl çalışılacağını açıklar.  
  
 [SQL Server ve ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 Özellikler ve SQL Server'a özel işlevler ile nasıl çalışılacağını açıklar.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Sağlayıcı-bağımsız kod yazmaya olanak tanıyan genel sınıfları açıklar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
