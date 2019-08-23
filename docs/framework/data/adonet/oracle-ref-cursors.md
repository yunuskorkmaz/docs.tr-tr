---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7c6b326b15a2af58da9206adf28070e57fec600c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963508"
---
# <a name="oracle-ref-cursors"></a>Oracle REF CURSOR
Oracle için .NET Framework Veri Sağlayıcısı Oracle **ref cursor** veri türünü destekler. Oracle REF IMLEÇLER ile çalışmak için veri sağlayıcısını kullanırken aşağıdaki davranışları göz önünde bulundurmanız gerekir.  
  
> [!NOTE]
> Bazı davranışlar Oracle için Microsoft OLE DB Sağlayıcısı (MSDAORA) farklıdır.  
  
- Performans nedenleriyle, Oracle için Veri Sağlayıcısı, açıkça belirtmediğiniz sürece MSDAORA olarak, **ref cursor** veri türlerini otomatik olarak bağlamayın.  
  
- Veri sağlayıcısı, REF CURSOR parametrelerini belirtmek için kullanılan {resultset} kaçış dahil olmak üzere herhangi bir ODBC kaçış dizisini desteklemez.  
  
- Ref imleçler döndüren bir saklı yordamı <xref:System.Data.OracleClient.OracleParameterCollection> yürütmek için, içindeki parametreleri **imlece** ve <xref:System.Data.OracleClient.OracleParameter.Direction%2A> <xref:System.Data.OracleClient.OracleType> **output**ile tanımlamanız gerekir. Veri sağlayıcısı yalnızca çıkış parametreleri olarak başvuru Imleçleri bağlamayı destekler. Sağlayıcı, giriş parametresi olarak başvuru Imleçleri desteklemez.  
  
- <xref:System.Data.OracleClient.OracleDataReader> Parametre değerinden alma desteklenmez. Değerler, komut yürütmeden sonra <xref:System.DBNull> türüdür.  
  
- REF imleçleri (örneğin, çağrılırken <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) ile birlikte kullanılan tek CommandBehavior numaralandırma değeri **CloseConnection**ise, diğerleri yok sayılır.  
  
- **OracleDataReader** 'Daki başvuru imleçlerinin sırası, **OracleParameterCollection**içindeki parametrelerin sırasına bağlıdır. <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Özellik yoksayıldı.  
  
- PL/SQL **tablo** veri türü desteklenmiyor. Ancak, REF Imleçleri daha etkilidir. **Tablo** veri türü kullanmanız GEREKIYORSA, msdaora ile OLE DB .NET veri sağlayıcısı kullanın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [REF CURSOR Örnekleri](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 REF IMLEÇLER kullanmayı gösteren üç örnek içerir.  
  
 [OracleDataReader’da REF CURSOR Parametreleri](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Bir başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve değeri bir **OracleDataReader**olarak okuduğunu gösterir.  
  
 [OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 İki başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve bir **OracleDataReader**kullanarak değerleri okuduğunu gösterir.  
  
 [Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 İki ref cursor parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini gösterir ve döndürülen satırlarla bir <xref:System.Data.DataSet> ile doldurur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
