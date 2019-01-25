---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 4dd0a78fafe63197987938021195723e3eed0885
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741002"
---
# <a name="oracle-ref-cursors"></a>Oracle REF CURSOR
Oracle, Oracle için .NET Framework veri sağlayıcısı sunuyor **REF CURSOR** veri türü. Oracle REF CURSOR ile çalışmak için veri sağlayıcısı'nı kullanarak, aşağıdaki davranışları düşünmelisiniz.  
  
> [!NOTE]
>  Bazı davranışları Microsoft OLE DB Sağlayıcısı'nın Oracle (MSDAORA) farklı.  
  
-   Performansla ilgili nedenlerle, Oracle için veri sağlayıcısı otomatik olarak bağlama **REF CURSOR** veri türleri, MSDAORA gibi bunları açıkça belirtmediğiniz sürece.  
  
-   Veri sağlayıcısı REF CURSOR parametreleri belirtmek için kullanılan {sonuç} kaçış dahil olmak üzere tüm ODBC kaçış dizileri desteklemez.  
  
-   REF CURSOR döndüren bir saklı yordamı yürütmek için parametreleri tanımlayın <xref:System.Data.OracleClient.OracleParameterCollection> ile bir <xref:System.Data.OracleClient.OracleType> , **imleç** ve <xref:System.Data.OracleClient.OracleParameter.Direction%2A> , **çıkış**. Veri sağlayıcısı, yalnızca çıkış parametreleri REF CURSOR bağlamayı destekler. Sağlayıcı REF CURSOR giriş parametreleri desteklemez.  
  
-   Alma bir <xref:System.Data.OracleClient.OracleDataReader> parametresinden değeri desteklenmiyor. Türünde değerleri olan <xref:System.DBNull> komut yürütmenin sonrasına.  
  
-   Yalnızca **CommandBehavior** REF CURSOR ile çalışan numaralandırma değeri (örneğin, çağrılırken <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) olan **CloseConnection**; diğerleri yoksayılır.  
  
-   REF CURSOR içinde sırasını **OracleDataReader** parametrelerinde bazında bağlıdır **OracleParameterCollection**. <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Özelliği yok sayılır.  
  
-   PL/SQL **tablo** veri türü desteklenmiyor. Ancak, REF CURSOR daha verimlidir. Kullanmanız gerekiyorsa bir **tablo** veri türü, OLE DB .NET veri sağlayıcısı MSDAORA ile kullanın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [REF CURSOR Örnekleri](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 REF CURSOR kullanarak gösteren üç örnekler içerir.  
  
 [OracleDataReader’da REF CURSOR Parametreleri](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Bir REF CURSOR parametresiyle döndürür ve olarak değeri okuyan bir PL/SQL saklı yordamı yürütme yapmayı gösteren bir **OracleDataReader**.  
  
 [OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 İki REF CURSOR parametreleri döndürür ve kullanarak değerlerini okur PL/SQL saklı yordamı yürütmek anlatan bir **OracleDataReader**.  
  
 [Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 İki REF CURSOR parametreleri döndürür ve dolduran bir PL/SQL saklı yordamı yürütme yapmayı gösteren bir <xref:System.Data.DataSet> satırlarla döndürülür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Oracle ve ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
