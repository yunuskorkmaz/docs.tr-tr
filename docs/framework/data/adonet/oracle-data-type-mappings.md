---
title: Oracle Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: be478741069e9edd406d73c0b75d5960b9909896
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783428"
---
# <a name="oracle-data-type-mappings"></a>Oracle Veri Türü Eşlemeleri
Aşağıdaki tabloda Oracle veri türleri ve bunların eşlemeleri <xref:System.Data.OracleClient.OracleDataReader>listelenmektedir.  
  
|Oracle veri türü|OracleDataReader. GetValue tarafından döndürülen veri türü .NET Framework|OracleDataReader. Getooyclevalue tarafından döndürülen OracleClient veri türü|Açıklamalar|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BDOSYA**|**Byte []**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte []**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Dize**|<xref:System.Data.OracleClient.OracleLob>||  
|**GÜNCEL**|**Hem**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Kategori**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü, **sayı** veri türü için bir diğer addır ve <xref:System.Data.OracleClient.OracleDataReader> bir System. Decimal veya <xref:System.Data.OracleClient.OracleNumber> kayan nokta değeri yerine bir **sistem. Decimal** öğesini döndürür. .NET Framework veri türünü kullanmak taşma oluşmasına neden olabilir.|  
|**GIR**|**Kategori**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü, **Number (38)** veri türü için bir diğer addır ve, <xref:System.Data.OracleClient.OracleDataReader> bir **System. Decimal** veya <xref:System.Data.OracleClient.OracleNumber> bir tamsayı değeri yerine bir. Decimal olacak şekilde tasarlanmıştır. .NET Framework veri türünü kullanmak taşma oluşmasına neden olabilir.|  
|**ARALIK YIL-AY**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**ARALIK GÜN-SANIYE**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**KALACAĞINI**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**UZUN HAM**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Dize**|<xref:System.Data.OracleClient.OracleLob>||  
|**SAYISINDAN**|**Kategori**|<xref:System.Data.OracleClient.OracleNumber>|.NET Framework veri türünü kullanmak taşma oluşmasına neden olabilir.|  
|**NVARCHAR2**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**MADDE**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**BAŞVURU IMLECI**|||Oracle **ref cursor** veri türü <xref:System.Data.OracleClient.OracleDataReader> nesne tarafından desteklenmiyor.|  
|**ROWID**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**ILIŞKIN**|**Hem**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**YEREL SAAT DILIMIYLE ZAMAN DAMGASI**|**Hem**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SAAT DILIMI ILE ZAMAN DAMGASI**|**Hem**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**IŞARETSIZ TAMSAYI**|**Sayı**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü, **Number (38)** veri türü için bir diğer addır ve, <xref:System.Data.OracleClient.OracleDataReader> bir System. Decimal veya <xref:System.Data.OracleClient.OracleNumber> işaretsiz tamsayı değeri yerine bir **sistem. Decimal** öğesini döndürür. .NET Framework veri türünü kullanmak taşma oluşmasına neden olabilir.|  
|**VARCHAR2**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
  
 Aşağıdaki tabloda Oracle veri türleri ve bunları parametre olarak bağlamada kullanılacak .NET Framework veri türleri (**System. Data. DbType** ve <xref:System.Data.OracleClient.OracleType>) listelenmektedir.  
  
|Oracle veri türü|Parametre olarak bağlanacak DbType numaralandırması|Parametre olarak bağlanacak OracleType numaralandırması|Açıklamalar|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BDOSYA**||**BDosya**|Oracle **yalnızca bir bDosya parametresi olarak** bir **bDosya** bağlamaya izin verir. Örneğin, **Byte []** veya <xref:System.Data.OracleClient.OracleBinary>gibi bir**Not olmayan bir değer bağlamaya** çalışırsanız, Oracle için .NET veri sağlayıcısı, sizin için otomatik olarak oluşturmaz.|  
|**BLOB**||**Blob**|Oracle yalnızca bir blobu blob **parametresi olarak** bağlamaya izin verir. , **Byte []** veya <xref:System.Data.OracleClient.OracleBinary>gibi**BLOB** olmayan bir değer bağlamaya çalışırsanız, Oracle için .NET veri sağlayıcısı sizin için otomatik olarak oluşturmaz.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**CLOB**|Oracle **yalnızca bir CLOB parametresi olarak** bir **CLOB** bağlamaya izin verir. Oracle için .NET Veri Sağlayıcısı, **System. String** veya <xref:System.Data.OracleClient.OracleString>gibi bir**CLOB** olmayan bir değer bağlamayı denerseniz sizin için otomatik olarak bir tane oluşturmaz.|  
|**GÜNCEL**|**Hem**|**Hem**||  
|**FLOAT**|**Single, Double, Decimal**|**Float, Double, sayı**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>**System. Data. DBType** ve ' i <xref:System.Data.OracleClient.OracleType>belirler.|  
|**GIR**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, sayı**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>**System. Data. DBType** ve ' i <xref:System.Data.OracleClient.OracleType>belirler.|  
|**ARALIK YIL-AY**|**Int32**|**Intermeyeartomonth**|<xref:System.Data.OracleClient.OracleType>yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**ARALIK GÜN-SANIYE**|**Nesne**|**Intertosecond**|<xref:System.Data.OracleClient.OracleType>yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**KALACAĞINI**|**Ansıtring**|**LongVarChar**||  
|**UZUN HAM**|**İkili**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle yalnızca bir **NCLOB** **NCLOB** parametresi olarak bağlamaya izin verir. Oracle için .NET Veri Sağlayıcısı, **System. String** veya <xref:System.Data.OracleClient.OracleString>gibi**NCLOB** olmayan bir değer bağlamaya çalışırsanız, sizin için otomatik olarak bir yapılandırma oluşturmaz.|  
|**SAYISINDAN**|**VarNumeric**|**Sayı**||  
|**NVARCHAR2**|**Dize**|**NVarChar**||  
|**MADDE**|**İkili**|**Madde**||  
|**BAŞVURU IMLECI**||**İmleç**|Daha fazla bilgi için bkz. [Oracle Ref imleçler](oracle-ref-cursors.md).|  
|**ROWID**|**Ansıtring**|**ROWID**||  
|**ILIŞKIN**|**Hem**|**İlişkin**|<xref:System.Data.OracleClient.OracleType>yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**YEREL SAAT DILIMIYLE ZAMAN DAMGASI**|**Hem**|**Zaman damgası yerel**|<xref:System.Data.OracleClient.OracleType>yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**SAAT DILIMI ILE ZAMAN DAMGASI**|**Hem**|**Zaman damgası Withtz**|<xref:System.Data.OracleClient.OracleType>yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**IŞARETSIZ TAMSAYI**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, uint32, sayı**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>**System. Data. DBType** ve ' i <xref:System.Data.OracleClient.OracleType>belirler.|  
|**VARCHAR2**|**Ansıtring**|**VarChar**||  
  
 <xref:System.Data.OracleClient.OracleParameter> Nesnenin <xref:System.Data.OracleClient.OracleParameter.Value%2A> özelliği tarafından kullanılan **InputOutput**, **output**ve **returnValue** **ParameterDirection** değerleri, giriş değeri bir Oracle veri türü olmadığı müddetçe .NET Framework veri türleridir ( örnek, <xref:System.Data.OracleClient.OracleNumber> veya <xref:System.Data.OracleClient.OracleString>). Bu, **ref cursor**, **bDosya**veya **lob** veri türleri için geçerlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
