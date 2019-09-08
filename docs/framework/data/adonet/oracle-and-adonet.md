---
title: Oracle ve ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: ccfe40f218e3f09de53d6cb596a31b2520d9ff9b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783479"
---
# <a name="oracle-and-adonet"></a>Oracle ve ADO.NET
> [!NOTE]
> İçindeki <xref:System.Data.OracleClient> türler kullanım dışıdır. Türler geçerli sürüm of.NET çerçevesinde desteklenmeye devam eder, ancak gelecekteki bir sürümde kaldırılacaktır. Microsoft, üçüncü taraf bir Oracle sağlayıcısı kullanmanızı önerir.  
  
 Bu bölümde, Oracle için .NET Framework Veri Sağlayıcısı özgü özellikler ve davranışlar açıklanmaktadır.  
  
 Oracle için .NET Framework Veri Sağlayıcısı Oracle Istemci yazılımı tarafından sağlanan Oracle Çağrı arabirimini (OCı) kullanarak bir Oracle veritabanına erişim sağlar. Veri sağlayıcısının işlevselliği, SQL Server, OLE DB ve ODBC için .NET Framework veri sağlayıcılarından benzer olacak şekilde tasarlanmıştır.  
  
 Oracle için .NET Framework veri sağlayıcısı kullanmak için, bir uygulamanın <xref:System.Data.OracleClient> ad alanına aşağıdaki şekilde başvurması gerekir:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Kodunuzu derlerken DLL 'ye bir başvuru de eklemeniz gerekir. Örneğin, bir C# program derlerken komut satırlarınız şunları içermelidir:  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sistem Gereksinimleri](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Oracle için .NET Framework Veri Sağlayıcısı kullanma gereksinimlerini açıklar ve bunu kullanırken bilinmesi gereken birçok sorunu açıklar.  
  
 [Oracle BFILE](oracle-bfiles.md)  
 Oracle BDOSYA veri türüyle çalışmak için kullanılan sınıfınıaçıklar.<xref:System.Data.OracleClient.OracleBFile>  
  
 [Oracle LOB](oracle-lobs.md)  
 Oracle LOB veri türleriyle çalışmak için kullanılan sınıfınıaçıklar.<xref:System.Data.OracleClient.OracleLob>  
  
 [Oracle REF CURSOR](oracle-ref-cursors.md)  
 Oracle REF CURSOR veri türü için desteği açıklar.  
  
 [OracleTypes](oracletypes.md)  
 <xref:System.Data.OracleClient.OracleNumber> Ve<xref:System.Data.OracleClient.OracleString>dahil Oracle veri türleriyle çalışmak için kullanabileceğiniz yapıları açıklar.  
  
 [Oracle Dizileri](oracle-sequences.md)  
 Sunucu tarafından oluşturulan anahtar Oracle sıra değerlerini alma desteğini açıklar.  
  
 [Oracle Veri Türü Eşlemeleri](oracle-data-type-mappings.md)  
 Oracle veri türlerini ve bunların eşlemelerini <xref:System.Data.OracleClient.OracleDataReader>listeler.  
  
 [Oracle Dağıtılmış İşlemleri](oracle-distributed-transactions.md)  
 Bir işlemin etkin <xref:System.Data.OracleClient.OracleConnection> olduğunu belirlerse, nesnenin var olan bir dağıtılmış işlemde otomatik olarak nasıl listeleneceğini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)  
 ADO.NET kullanılırken güvenli kodlama uygulamalarını açıklar.  
  
 [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)  
 ' `DataSets`Nin nasıl oluşturulduğunu ve kullanılacağını açıklar, `DataSets` `DataTables`türü, ve `DataViews`.  
  
 [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)  
 ADO.NET içindeki verilerle nasıl çalışabileceğinizi açıklar.  
  
 [SQL Server ve ADO.NET](./sql/index.md)  
 SQL Server özgü özellikler ve işlevlerle nasıl çalışabileceğinizi açıklar.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 ADO.NET ' de sağlayıcıya bağımsız kod yazmanıza izin veren genel sınıfları açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
