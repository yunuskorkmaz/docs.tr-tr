---
description: 'Daha fazla bilgi edinin: Oracle veri türü eşlemeleri'
title: Oracle Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: 1b5a130916a54049518b8b335fbf384d99035090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754374"
---
# <a name="oracle-data-type-mappings"></a>Oracle Veri Türü Eşlemeleri

Aşağıdaki tabloda Oracle veri türleri ve bunların eşlemeleri listelenmektedir <xref:System.Data.OracleClient.OracleDataReader> .  
  
|Oracle veri türü|OracleDataReader. GetValue tarafından döndürülen veri türü .NET Framework|OracleDataReader. Getooyclevalue tarafından döndürülen OracleClient veri türü|Açıklamalar|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BDosya**|**Byte []**|<xref:System.Data.OracleClient.OracleBFile>||  
|**Bun**|**Byte []**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Dize**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**Tarih Saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Kategori**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü, **sayı** veri türü için bir diğer addır ve bir <xref:System.Data.OracleClient.OracleDataReader> **System. Decimal** veya <xref:System.Data.OracleClient.OracleNumber> kayan nokta değeri yerine bir sistem. Decimal öğesini döndürür. .NET Framework veri türünü kullanmak taşma oluşmasına neden olabilir.|  
|**GIR**|**Kategori**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü, **Number (38)** veri türü için bir diğer addır ve, bir <xref:System.Data.OracleClient.OracleDataReader> **System. Decimal** veya bir <xref:System.Data.OracleClient.OracleNumber> tamsayı değeri yerine bir. Decimal olacak şekilde tasarlanmıştır. .NET Framework veri türünü kullanmak taşma oluşmasına neden olabilir.|  
|**ARALıK YıL-AY**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**ARALıK GÜN-SANIYE**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**KALACAĞıNı**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**UZUN HAM**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Dize**|<xref:System.Data.OracleClient.OracleLob>||  
|**SAYıSıNDAN**|**Kategori**|<xref:System.Data.OracleClient.OracleNumber>|.NET Framework veri türünü kullanmak taşma oluşmasına neden olabilir.|  
|**NVARCHAR2**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**Madde**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**BAŞVURU IMLECI**|||Oracle **ref cursor** veri türü nesne tarafından desteklenmiyor <xref:System.Data.OracleClient.OracleDataReader> .|  
|**ROWıD**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**Tarih Saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**YEREL SAAT DILIMIYLE ZAMAN DAMGASı**|**Tarih Saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SAAT DILIMI ILE ZAMAN DAMGASı**|**Tarih Saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**IŞARETSIZ TAMSAYı**|**Sayı**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü, **Number (38)** veri türü için bir diğer addır ve, <xref:System.Data.OracleClient.OracleDataReader> bir **System. Decimal** veya <xref:System.Data.OracleClient.OracleNumber> işaretsiz tamsayı değeri yerine bir sistem. Decimal öğesini döndürür. .NET Framework veri türünü kullanmak taşma oluşmasına neden olabilir.|  
|**VARCHAR2**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
  
 Aşağıdaki tabloda Oracle veri türleri ve bunları parametre olarak bağlamada kullanılacak .NET Framework veri türleri (**System. Data. DbType** ve <xref:System.Data.OracleClient.OracleType> ) listelenmektedir.  
  
|Oracle veri türü|Parametre olarak bağlanacak DbType numaralandırması|Parametre olarak bağlanacak OracleType numaralandırması|Açıklamalar|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BDosya**||**BDosya**|Oracle **yalnızca bir bDosya parametresi olarak** bir **bDosya** bağlamaya izin verir. Örneğin, **Byte []** veya gibi bir **Not olmayan bir değer bağlamaya** çalışırsanız, Oracle için .NET veri sağlayıcısı, sizin için otomatik olarak oluşturmaz <xref:System.Data.OracleClient.OracleBinary> .|  
|**Bun**||**Blob**|Oracle yalnızca bir blobu blob **parametresi olarak** bağlamaya  izin verir. , **Byte []** veya gibi **BLOB** olmayan bir değer bağlamaya çalışırsanız, Oracle için .NET veri sağlayıcısı sizin için otomatik olarak oluşturmaz <xref:System.Data.OracleClient.OracleBinary> .|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**CLOB**|Oracle **yalnızca bir CLOB parametresi olarak** bir **CLOB** bağlamaya izin verir. Oracle için .NET Veri Sağlayıcısı, **System. String** veya gibi bir **CLOB** olmayan bir değer bağlamayı denerseniz sizin için otomatik olarak bir tane oluşturmaz <xref:System.Data.OracleClient.OracleString> .|  
|**DATE**|**Tarih Saat**|**Tarih Saat**||  
|**FLOAT**|**Single, Double, Decimal**|**Float, Double, sayı**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>**System. Data. DBType** ve ' i belirler <xref:System.Data.OracleClient.OracleType> .|  
|**GIR**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, sayı**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>**System. Data. DBType** ve ' i belirler <xref:System.Data.OracleClient.OracleType> .|  
|**ARALıK YıL-AY**|**Int32**|**Intermeyeartomonth**|<xref:System.Data.OracleClient.OracleType> yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**ARALıK GÜN-SANIYE**|**Nesne**|**Intertosecond**|<xref:System.Data.OracleClient.OracleType> yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**KALACAĞıNı**|**Ansıtring**|**LongVarChar**||  
|**UZUN HAM**|**İkili**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle yalnızca bir **NCLOB** **NCLOB** parametresi olarak bağlamaya izin verir. Oracle için .NET Veri Sağlayıcısı, **System. String** veya gibi **NCLOB** olmayan bir değer bağlamaya çalışırsanız, sizin için otomatik olarak bir yapılandırma oluşturmaz <xref:System.Data.OracleClient.OracleString> .|  
|**SAYıSıNDAN**|**VarNumeric**|**Sayı**||  
|**NVARCHAR2**|**Dize**|**NVarChar**||  
|**Madde**|**İkili**|**Ham**||  
|**BAŞVURU IMLECI**||**Oraya**|Daha fazla bilgi için bkz. [Oracle Ref imleçler](oracle-ref-cursors.md).|  
|**ROWıD**|**Ansıtring**|**ROWID**||  
|**TIMESTAMP**|**Tarih Saat**|**İlişkin**|<xref:System.Data.OracleClient.OracleType> yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**YEREL SAAT DILIMIYLE ZAMAN DAMGASı**|**Tarih Saat**|**Zaman damgası yerel**|<xref:System.Data.OracleClient.OracleType> yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**SAAT DILIMI ILE ZAMAN DAMGASı**|**Tarih Saat**|**Zaman damgası Withtz**|<xref:System.Data.OracleClient.OracleType> yalnızca Oracle 9i istemcisi ve sunucu yazılımı kullanılırken kullanılabilir.|  
|**IŞARETSIZ TAMSAYı**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, uint32, sayı**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>**System. Data. DBType** ve ' i belirler <xref:System.Data.OracleClient.OracleType> .|  
|**VARCHAR2**|**Ansıtring**|**VarChar**||  
  
 Nesnenin özelliği tarafından kullanılan **InputOutput**, **output** ve **returnValue** **ParameterDirection** değerleri <xref:System.Data.OracleClient.OracleParameter.Value%2A> <xref:System.Data.OracleClient.OracleParameter> , giriş değeri bir Oracle veri türü (örneğin, veya) olmadığı takdirde .NET Framework veri türleridir <xref:System.Data.OracleClient.OracleNumber> <xref:System.Data.OracleClient.OracleString> . Bu, **ref cursor**, **bDosya** veya **lob** veri türleri için geçerlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
