---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7cd29a6a20015c7ce4475b0211cb07f7ee78b530
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794877"
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
 [REF CURSOR Örnekleri](ref-cursor-examples.md)  
 REF IMLEÇLER kullanmayı gösteren üç örnek içerir.  
  
 [OracleDataReader’da REF CURSOR Parametreleri](ref-cursor-parameters-in-an-oracledatareader.md)  
 Bir başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve değeri bir **OracleDataReader**olarak okuduğunu gösterir.  
  
 [OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma](retrieving-data-from-multiple-ref-cursors.md)  
 İki başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve bir **OracleDataReader**kullanarak değerleri okuduğunu gösterir.  
  
 [Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma](filling-a-dataset-using-one-or-more-ref-cursors.md)  
 İki ref cursor parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini gösterir ve döndürülen satırlarla bir <xref:System.Data.DataSet> ile doldurur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
