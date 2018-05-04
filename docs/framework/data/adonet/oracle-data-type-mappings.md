---
title: Oracle veri türü Mappings1
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: 2b5a3a90c704dd6edf32e6fb77b551e6fc0f78ec
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-data-type-mappings"></a>Oracle veri türü eşlemeleri
Oracle veri türlerini ve eşlemelerini için aşağıdaki tabloda listelenmektedir <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Oracle veri türü|OracleDataReader.GetValue tarafından döndürülen .NET framework veri türü|OracleDataReader.GetOracleValue tarafından döndürülen OracleClient veri türü|Açıklamalar|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BDOSYA**|**Byte]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Dize**|<xref:System.Data.OracleClient.OracleLob>||  
|**TARİH**|**Tarih saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**KAYAN NOKTA**|**Ondalık**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü için bir diğer ad olan **numarası** veri türü ve tasarlanmıştır böylece <xref:System.Data.OracleClient.OracleDataReader> döndürür bir **System.Decimal** veya <xref:System.Data.OracleClient.OracleNumber> bir kayan nokta değeri yerine. .NET Framework veri türünü kullanarak taşma neden olabilir.|  
|**TAMSAYI**|**Ondalık**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü için bir diğer ad olan **NUMBER(38)** veri türü ve tasarlanmıştır böylece <xref:System.Data.OracleClient.OracleDataReader> döndürür bir **System.Decimal** veya <xref:System.Data.OracleClient.OracleNumber> yerine bir tamsayı değeri. .NET Framework veri türünü kullanarak taşma neden olabilir.|  
|**ARALIĞI YIL AY İÇİN**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**İKİNCİ GÜN ARALIĞI**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**UZUN**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**UZUN HAM**|**Byte]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Dize**|<xref:System.Data.OracleClient.OracleLob>||  
|**SAYI**|**Ondalık**|<xref:System.Data.OracleClient.OracleNumber>|.NET Framework veri türünü kullanarak taşma neden olabilir.|  
|**NVARCHAR2**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**HAM**|**Byte]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF İMLEÇ**|||Oracle **REF İMLEÇ** veri türü tarafından desteklenmiyor <xref:System.Data.OracleClient.OracleDataReader> nesnesi.|  
|**SATIR KİMLİĞİ**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
|**ZAMAN DAMGASI**|**Tarih saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**YEREL SAAT DİLİMİ ZAMAN DAMGASI**|**Tarih saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SAAT DİLİMİ ZAMAN DAMGASI**|**Tarih saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**İŞARETSİZ TAMSAYI**|**Sayı**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü için bir diğer ad olan **NUMBER(38)** veri türü ve tasarlanmıştır böylece <xref:System.Data.OracleClient.OracleDataReader> döndürür bir **System.Decimal** veya <xref:System.Data.OracleClient.OracleNumber> yerine bir işaretsiz tamsayı değeri. .NET Framework veri türünü kullanarak taşma neden olabilir.|  
|**VARCHAR2**|**Dize**|<xref:System.Data.OracleClient.OracleString>||  
  
 Oracle veri türleri ve .NET Framework veri türleri aşağıdaki tabloda listelenmektedir (**System.Data.DbType** ve <xref:System.Data.OracleClient.OracleType>) parametre olarak bağlama sırasında kullanılacak.  
  
|Oracle veri türü|Parametre olarak bağlamak için DbType numaralandırması|Parametre olarak bağlamak için OracleType numaralandırması|Açıklamalar|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BDOSYA**||**BDosya**|Oracle yalnızca bağlama sağlayan bir **BDOSYA** olarak bir **BDOSYA** parametresi. Bağlı olmayan bir çalışırsanız, Oracle için .NET veri sağlayıcısı otomatik olarak sizin için bir oluşturmak değil**BDOSYA** gibi değerini **byte []** veya <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**BLOB**|Oracle yalnızca bağlama sağlayan bir **BLOB** olarak bir **BLOB** parametresi. Bağlı olmayan bir çalışırsanız, Oracle için .NET veri sağlayıcısı otomatik olarak sizin için bir oluşturmak değil**BLOB** gibi değerini **byte []** veya <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**char**||  
|**CLOB**||**CLOB**|Oracle yalnızca bağlama sağlayan bir **CLOB** olarak bir **CLOB** parametresi. Bağlı olmayan bir çalışırsanız, Oracle için .NET veri sağlayıcısı otomatik olarak sizin için bir oluşturmak değil**CLOB** gibi değerini **System.String** veya <xref:System.Data.OracleClient.OracleString>.|  
|**TARİH**|**Tarih saat**|**Tarih saat**||  
|**KAYAN NOKTA**|**, Double, Decimal tek**|**Float, çift, numara**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> belirler **System.Data.DBType** ve <xref:System.Data.OracleClient.OracleType>.|  
|**TAMSAYI**|**SByte, Int16, Int32, Int64, ondalık**|**SByte, Int16, Int32, numara**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> belirler **System.Data.DBType** ve <xref:System.Data.OracleClient.OracleType>.|  
|**ARALIĞI YIL AY İÇİN**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**İKİNCİ GÜN ARALIĞI**|**Nesne**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**UZUN**|**AnsiString**|**LongVarChar**||  
|**UZUN HAM**|**İkili**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle yalnızca bağlama sağlayan bir **NCLOB** olarak bir **NCLOB** parametresi. Bağlı olmayan bir çalışırsanız, Oracle için .NET veri sağlayıcısı otomatik olarak sizin için bir oluşturmak değil**NCLOB** gibi değerini **System.String** veya <xref:System.Data.OracleClient.OracleString>.|  
|**SAYI**|**VarNumeric**|**Sayı**||  
|**NVARCHAR2**|**Dize**|**NVarChar**||  
|**HAM**|**İkili**|**Ham**||  
|**REF İMLEÇ**||**İmleç**|Daha fazla bilgi için bkz: [Oracle REF imleçler](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**SATIR KİMLİĞİ**|**AnsiString**|**Satır kimliği**||  
|**ZAMAN DAMGASI**|**Tarih saat**|**zaman damgası**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**YEREL SAAT DİLİMİ ZAMAN DAMGASI**|**Tarih saat**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**SAAT DİLİMİ ZAMAN DAMGASI**|**Tarih saat**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**İŞARETSİZ TAMSAYI**|**UInt16 UInt32, UInt64, ondalık bayt**|**Bayt, UInt16, Uint32, numara**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> belirler **System.Data.DBType** ve <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Giriş/çıkış**, **çıkış**, ve **ReturnValue** **ParameterDirection** tarafından kullanılan değerleri <xref:System.Data.OracleClient.OracleParameter.Value%2A> özelliği<xref:System.Data.OracleClient.OracleParameter> nesne olan .NET Framework veri türleri, giriş değeri bir Oracle veri türü değilse (örneğin, <xref:System.Data.OracleClient.OracleNumber> veya <xref:System.Data.OracleClient.OracleString>). Bu geçerli değildir **REF İMLEÇ**, **BDOSYA**, veya **LOB** veri türleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oracle ve ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
