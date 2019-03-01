---
title: Oracle veri türü eşlemeleri
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: d5e13b0ff4f9c3d5cc145abd4f0bcc3d8e717ca1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965781"
---
# <a name="oracle-data-type-mappings"></a>Oracle veri türü eşlemeleri
Aşağıdaki tabloda, Oracle veri türleri ve eşleşmeleri listeler <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Oracle veri türü|.NET framework veri türü tarafından OracleDataReader.GetValue döndürdü|OracleDataReader.GetOracleValue tarafından döndürülen OracleClient veri türü|Açıklamalar|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BDOSYA**|**Bayt]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Bayt]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**dize**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**dize**|<xref:System.Data.OracleClient.OracleLob>||  
|**TARİH**|**Tarih/saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**KAYAN NOKTA**|**Ondalık**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü için bir diğer ad, **numarası** veri türü ve böylece <xref:System.Data.OracleClient.OracleDataReader> döndürür bir **System.Decimal** veya <xref:System.Data.OracleClient.OracleNumber> yerine bir kayan nokta değeri. .NET Framework veri türü kullanan bir taşma neden olabilir.|  
|**TAMSAYI**|**Ondalık**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü için bir diğer ad, **NUMBER(38)** veri türü ve böylece <xref:System.Data.OracleClient.OracleDataReader> döndürür bir **System.Decimal** veya <xref:System.Data.OracleClient.OracleNumber> yerine bir tamsayı değeri. .NET Framework veri türü kullanan bir taşma neden olabilir.|  
|**YIL AY ARALIĞI**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**İKİNCİ GÜN ARALIĞI**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**UZUN**|**dize**|<xref:System.Data.OracleClient.OracleString>||  
|**UZUN HAM**|**Bayt]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**dize**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**dize**|<xref:System.Data.OracleClient.OracleLob>||  
|**SAYI**|**Ondalık**|<xref:System.Data.OracleClient.OracleNumber>|.NET Framework veri türü kullanan bir taşma neden olabilir.|  
|**NVARCHAR2**|**dize**|<xref:System.Data.OracleClient.OracleString>||  
|**HAM**|**Bayt]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Oracle **REF CURSOR** veri türü tarafından desteklenmiyor <xref:System.Data.OracleClient.OracleDataReader> nesne.|  
|**SATIR KİMLİĞİ**|**dize**|<xref:System.Data.OracleClient.OracleString>||  
|**ZAMAN DAMGASI**|**Tarih/saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**YEREL SAAT DİLİMİ İLE ZAMAN DAMGASI**|**Tarih/saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**SAAT DİLİMİ İLE ZAMAN DAMGASI**|**Tarih/saat**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**İŞARETSİZ TAMSAYI**|**Sayı**|<xref:System.Data.OracleClient.OracleNumber>|Bu veri türü için bir diğer ad, **NUMBER(38)** veri türü ve böylece <xref:System.Data.OracleClient.OracleDataReader> döndürür bir **System.Decimal** veya <xref:System.Data.OracleClient.OracleNumber> yerine bir işaretsiz tamsayı değeri. .NET Framework veri türü kullanan bir taşma neden olabilir.|  
|**VARCHAR2**|**dize**|<xref:System.Data.OracleClient.OracleString>||  
  
 Oracle veri türleri ve .NET Framework veri türleri aşağıdaki tabloda listelenmektedir (**System.Data.DbType** ve <xref:System.Data.OracleClient.OracleType>) bunları parametre olarak bağlanırken kullanmak üzere.  
  
|Oracle veri türü|Bir parametre olarak bağlamak için DbType numaralandırması|Bir parametre olarak bağlamak için OracleType numaralandırması|Açıklamalar|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BDOSYA**||**BDosya**|Oracle, bağlama yalnızca sağlayan bir **BDOSYA** olarak bir **BDOSYA** parametresi. Olmayan bir bağlama denerseniz, Oracle için .NET veri sağlayıcısı otomatik olarak sizin için bir tane oluşturmak değil**BDOSYA** gibi değerini **byte []** veya <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|Oracle, bağlama yalnızca sağlayan bir **BLOB** olarak bir **BLOB** parametresi. Olmayan bir bağlama denerseniz, Oracle için .NET veri sağlayıcısı otomatik olarak sizin için bir tane oluşturmak değil**BLOB** gibi değerini **byte []** veya <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**CLOB**|Oracle, bağlama yalnızca sağlayan bir **CLOB** olarak bir **CLOB** parametresi. Olmayan bir bağlama denerseniz, Oracle için .NET veri sağlayıcısı otomatik olarak sizin için bir tane oluşturmak değil**CLOB** gibi değerini **System.String** veya <xref:System.Data.OracleClient.OracleString>.|  
|**TARİH**|**Tarih/saat**|**Tarih/saat**||  
|**KAYAN NOKTA**|**, Double, Decimal tek**|**Kayan, çift, numara**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> belirler **System.Data.DBType** ve <xref:System.Data.OracleClient.OracleType>.|  
|**TAMSAYI**|**SByte, Int16, Int32, Int64, ondalık**|**SByte, Int16, Int32, numara**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> belirler **System.Data.DBType** ve <xref:System.Data.OracleClient.OracleType>.|  
|**YIL AY ARALIĞI**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**İKİNCİ GÜN ARALIĞI**|**Nesne**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**UZUN**|**AnsiString**|**LongVarChar**||  
|**UZUN HAM**|**İkili**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**nChar**||  
|**NCLOB**||**NClob**|Oracle, bağlama yalnızca sağlayan bir **NCLOB** olarak bir **NCLOB** parametresi. Olmayan bir bağlama denerseniz, Oracle için .NET veri sağlayıcısı otomatik olarak sizin için bir tane oluşturmak değil**NCLOB** gibi değerini **System.String** veya <xref:System.Data.OracleClient.OracleString>.|  
|**SAYI**|**VarNumeric**|**Sayı**||  
|**NVARCHAR2**|**dize**|**NVarChar**||  
|**HAM**|**İkili**|**Ham**||  
|**REF CURSOR**||**İmleç**|Daha fazla bilgi için [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md).|  
|**SATIR KİMLİĞİ**|**AnsiString**|**Satır kimliği**||  
|**ZAMAN DAMGASI**|**Tarih/saat**|**Zaman damgası**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**YEREL SAAT DİLİMİ İLE ZAMAN DAMGASI**|**Tarih/saat**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**SAAT DİLİMİ İLE ZAMAN DAMGASI**|**Tarih/saat**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> Yalnızca kullanılabilir olduğunda, her iki Oracle 9i istemci ve sunucu yazılımı kullanıyor.|  
|**İŞARETSİZ TAMSAYI**|**Byte, Uınt16, Uınt32, Uınt64, ondalık**|**Byte, Uınt16, UInt32, numara**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> belirler **System.Data.DBType** ve <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 **Giriş/çıkış**, **çıkış**, ve **ReturnValue** **ParameterDirection** tarafından kullanılan değerleri <xref:System.Data.OracleClient.OracleParameter.Value%2A> özelliği<xref:System.Data.OracleClient.OracleParameter> nesne olan .NET Framework veri türleri, giriş değeri bir Oracle veri türü değilse (örneğin, <xref:System.Data.OracleClient.OracleNumber> veya <xref:System.Data.OracleClient.OracleString>). Bu geçerli değildir **REF CURSOR**, **BDOSYA**, veya **LOB** veri türleri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Oracle ve ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
