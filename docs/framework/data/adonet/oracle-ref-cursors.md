---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: cbf330ba381a825c2d16038c01d7bdc52bc8f482
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180887"
---
# <a name="oracle-ref-cursors"></a>Oracle REF CURSOR

Oracle için .NET Framework Veri Sağlayıcısı Oracle **ref cursor** veri türünü destekler. Oracle REF IMLEÇLER ile çalışmak için veri sağlayıcısını kullanırken aşağıdaki davranışları göz önünde bulundurmanız gerekir.  
  
> [!NOTE]
> Bazı davranışlar Oracle için Microsoft OLE DB Sağlayıcısı (MSDAORA) farklıdır.  
  
- Performans nedenleriyle, Oracle için Veri Sağlayıcısı, açıkça belirtmediğiniz sürece MSDAORA olarak, **ref cursor** veri türlerini otomatik olarak bağlamayın.  
  
- Veri sağlayıcısı, REF CURSOR parametrelerini belirtmek için kullanılan {resultset} kaçış dahil olmak üzere herhangi bir ODBC kaçış dizisini desteklemez.  
  
- REF IMLEÇLER döndüren bir saklı yordamı yürütmek için, içindeki parametreleri <xref:System.Data.OracleClient.OracleParameterCollection> <xref:System.Data.OracleClient.OracleType> **Imlece** ve <xref:System.Data.OracleClient.OracleParameter.Direction%2A> **output**ile tanımlamanız gerekir. Veri sağlayıcısı yalnızca çıkış parametreleri olarak başvuru Imleçleri bağlamayı destekler. Sağlayıcı, giriş parametresi olarak başvuru Imleçleri desteklemez.  
  
- <xref:System.Data.OracleClient.OracleDataReader>Parametre değerinden alma desteklenmez. Değerler, <xref:System.DBNull> komut yürütmeden sonra türüdür.  
  
- REF Imleçleri (örneğin, çağrılırken) ile birlikte kullanılan tek **CommandBehavior** numaralandırma değeri <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> **CloseConnection**ise, diğerleri yok sayılır.  
  
- **OracleDataReader** 'Daki başvuru imleçlerinin sırası, **OracleParameterCollection**içindeki parametrelerin sırasına bağlıdır. <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A>Özellik yoksayıldı.  
  
- PL/SQL **tablo** veri türü desteklenmiyor. Ancak, REF Imleçleri daha etkilidir. **Tablo** veri türü kullanmanız GEREKIYORSA, msdaora ile OLE DB .NET veri sağlayıcısı kullanın.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [REF CURSOR Örnekleri](ref-cursor-examples.md)  
 REF IMLEÇLER kullanmayı gösteren üç örnek içerir.  
  
 [OracleDataReader’da REF CURSOR Parametreleri](ref-cursor-parameters-in-an-oracledatareader.md)  
 Bir başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve değeri bir **OracleDataReader**olarak okuduğunu gösterir.  
  
 [OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma](retrieving-data-from-multiple-ref-cursors.md)  
 İki başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve bir **OracleDataReader**kullanarak değerleri okuduğunu gösterir.  
  
 [Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma](filling-a-dataset-using-one-or-more-ref-cursors.md)  
 İki REF CURSOR parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini gösterir ve <xref:System.Data.DataSet> döndürülen satırlarla bir ile doldurur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
